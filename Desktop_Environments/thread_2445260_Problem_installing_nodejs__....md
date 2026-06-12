---
title: "Problem installing nodejs  ..."
date: 2020-06-11
forum: Desktop Environments
---

### Post by dbee on 2020-06-11
So i'm testing a plugin and i want to create a docker instance of wordpress in the root directory of the plugin with

```
wp-env start
```

I'm on ubuntu 20.04 LTS, i've installed npm and nodejs.

```

dara@hp-laptop-ubuntu-20-04-lts:~$ npm -v
6.14.4
dara@hp-laptop-ubuntu-20-04-lts:~$ nodejs -v
v10.19.0

```
however when i try to start the instance I get 

```

dara@hp-laptop-ubuntu-20-04-lts:~$ wp-env start
internal/modules/cjs/loader.js:638
    throw err;
    ^

Error: Cannot find module '../build/Debug/nodegit.node'
    at Function.Module._resolveFilename (internal/modules/cjs/loader.js:636:15)
    at Function.Module._load (internal/modules/cjs/loader.js:562:25)
    at Module.require (internal/modules/cjs/loader.js:692:17)
    at require (internal/modules/cjs/helpers.js:25:18)
    at Object.<anonymous> (/usr/local/lib/node_modules/@wordpress/env/node_modules/nodegit/dist/nodegit.js:19:12)
    at Module._compile (internal/modules/cjs/loader.js:778:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)

```

There's a nodegit.node in Build/Release but not in Debug folder with nodegit in it ...

---

### Post by dbee on 2020-06-12
Somehow the directory tree for nodejs build/Debug folder got removed with an old wordpress plugin

Found it again with a
```

find -iname 'nodegit.node' -type f

```
Then just copied it back into the
```

usr/local/lib/node_modules/@wordpress/env/node_modules/

```
path and everything was OK again ...

---

