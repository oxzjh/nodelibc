# nodelib

## Usage:
```
// Add this line in your entry file.
require('compilec');
```

#### 1. Useful functions, such as "trim","md5","requestGet" and so on...
```
const nodelib = require('nodelibc');

console.log(nodelib.md5('123456'));
```

#### 2. Cache
```
const nodelib = require('nodelibc');

global.cache = new nodelib.Cache('cachefile.json');

cache.set('key1', 'some value');
cache.incr('key2');

console.log(cache.get('key1'));
console.log(cache.get('key2'));

cache.save(true); // sync save cache to file
```

#### 3. Http
```
const nodelib = require('nodelibc');

const server = new nodelib.Http(3000, (res, data, req) => {
    console.log(data);
    server.send(res, 'Hello World!');
});
```

#### 4. Https
```
const fs = require('fs');
const nodelib = require('nodelibc');

const server = new nodelib.Https({
        key:fs.readFileSync('your key pem path.'),
        cert:fs.readFileSync('your cert pem path.')
    }, 3000, (res, data, req) => {
        console.log(data);
        server.send(res, 'Hello World!');
    }
);
```

#### 5. Udp
```
const nodelib = require('nodelibc');
const server = new nodelib.Udp(3000, (rinfo, data) => {
    console.log(data);
    server.send(rinfo, 'Hello World!');
});
```

#### 6. SocketTCP
```
const nodelib = require('nodelibc');
const server = new nodelib.SocketTCP(3000, (socket, data) => {
    console.log(data);
    server.send(socket, 'Got message');
    server.broadcast('Hello World!');
});
```

#### 7. SocketWS
```
// npm install ws
const nodelib = require('nodelibc');
const server = new nodelib.SocketWS(3000, (socket, data) => {
    console.log(data);
    server.send(socket, 'Got message');
    server.broadcast('Hello World!');
});
```

#### 8. Redis
```
// npm install redis
const nodelib = require('nodelibc');

global.redis = new nodelib.Redis({
    host:'127.0.0.1',
    // password:'',
    db:1,
    prefix:'prefix_'
});

redis.set('key1', 'some value', 5);
redis.incr('key2');

console.log(cache.get('key1'));
console.log(cache.get('key2'));
```

#### 9. Mysql
```
// npm install mysql
const nodelib = require('nodelibc');

global.mysql = new nodelib.Mysql('127.0.0.1', 'root', 'root', 'test');

mysql.getArray('SELECT * FROM user', users => {
    console.log(users);
});
```