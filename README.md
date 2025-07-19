# FakeRESTApi
A simple 10 second NodeJS fake json REST api configuration

## Beginning steps

Set up NodeJS

```
sudo apt install nodejs
```

Set up npm

```
sudo apt install npm
```

Set up JSON Server 

```
npm install -g json-server
```

Build a `db.json` file with some data

```json
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
```

Launch JSON Server

```bash
json-server --watch db.json
```

Navigate to [http://localhost:3000](http://localhost:3000) to examine all the generated APIs and the returned data
Example: If you navigate to [http://localhost:3000/posts/1](http://localhost:3000/posts/1), you'll receive

```json
{ "id": 1, "title": "json-server", "author": "typicode" }
```

Additionally when performing requests, it's beneficial to understand that:

- If you perform POST, PUT, PATCH or DELETE requests, modifications will be automatically and safely stored to `db.json` utilizing [lowdb](https://github.com/typicode/lowdb).
- Your request body JSON should be object enclosed, just like the GET output. (for example `{"name": "Foobar"}`)
- Id values are not mutable. Any `id` value in the body of your PUT or PATCH request will be ignored. Only a value set in a POST request will be respected, but only if not already taken.
- A POST, PUT or PATCH request should include a `Content-Type: application/json` header to utilize the JSON in the request body. Otherwise it will result in a 200 OK but without modifications being applied to the data.