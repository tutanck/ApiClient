<h1 align="center">Welcome to axios-api-client-gen 👋</h1>
<p>
  <img alt="Version" src="https://img.shields.io/badge/version-1.0.0-blue.svg?cacheSeconds=2592000" />
</p>

> Generate complete api client from express route map using axios

## Install

```sh
npm i axios-api-client-gen
```

## How it works

Asume you have an express route map like this ([see example here](https://github.com/expressjs/express/blob/4.13.1/examples/route-map/index.js#L52-L66)):

```Javascript
const api = {
  '/users': {
    get: users.list,
    delete: users.delete,
    '/:uid': {
      get: users.get,
      '/pets': {
        get: pets.list,
        '/:pid': {
          delete: pets.delete
        }
      }
    }
  }
};

app.map(api);
```

With `axios-api-client-gen` you can generate the complete api-client in seconds.

## Usage

```Javascript
const gen = require('axios-api-client-gen');

// gen('path/to/file.js', apiMap)
gen('./client/index.js', api);

```

## Expected Result

> A file `'./client/index.js'` containing :

```Javascript
// Wed Sep 25 2019 21:44:36 GMT+0200 (GMT+02:00)

import axios from 'axios';

const API_BASE_URL = process.env.API_BASE_URL;

export function get_users(...options) {
  return axios({
    baseURL: API_BASE_URL,
    method: 'get',
    url: `/users`,
    ...options,
  });
}

export function delete_users(...options) {
  return axios({
    baseURL: API_BASE_URL,
    method: 'delete',
    url: `/users`,
    ...options,
  });
}

export function get_users_by_uid(uid, ...options) {
  return axios({
    baseURL: API_BASE_URL,
    method: 'get',
    url: `/users/${uid}`,
    ...options,
  });
}

export function get_users_by_uid_pets(uid, ...options) {
  return axios({
    baseURL: API_BASE_URL,
    method: 'get',
    url: `/users/${uid}/pets`,
    ...options,
  });
}

export function delete_users_by_uid_pets_by_pid(uid, pid, ...options) {
  return axios({
    baseURL: API_BASE_URL,
    method: 'delete',
    url: `/users/${uid}/pets/${pid}`,
    ...options,
  });
}
```

## Full Working Example 
> You can checkout the full working example [HERE](https://github.com/tutanck/axios-api-client-gen-example)

## Author

👤 **tutanck**

- Twitter: [@tutanck](https://twitter.com/tutanck)
- Github: [@tutanck](https://github.com/tutanck)

## 🤝 Contributing

Contributions, issues and feature requests are welcome!<br />I recently fell in ❤️ with [25](https://open.spotify.com/album/0UJsvx1tZnZRmcpzaG3wRH?si=YcMrV_OxRMuxAtFxqlOptw) and issues! <br />Feel free to check [issues page](https://github.com/tutanck/axios-api-client-gen/issues).

## Show your support

Give a ⭐️ if this project helped you!

---

_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
