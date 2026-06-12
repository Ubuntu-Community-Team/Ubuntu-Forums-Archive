---
title: "Dependency prob: Its installed, but it says it isn't"
date: 2005-11-12
forum: Desktop Environments
---

### Post by grizzly on 2005-11-12
After exploring a bit it turns out all my dependency problems comes down to libc6 not installed to the required version.
```
Depends: libc6 (=2.3.2.ds1-20ubuntu14) but 2.3.5-1ubuntu12 is to be installed
```

Synaptic shows that i have the latest version(2.3.5) of libc6 so there nothing that  i can do  here :( . In other words i am stuck . I have this prob for a few days now, searched everywhere but found no solutions.

Also (this could be related)
apt-get update gives the error:
```
Get:4 http://archive.ubuntu.com hoary/universe Sources [1142kB]
99% [4 Sources gzip 0]                                               8789B/s 0s
**gzip: stdin: not in gzip format**

```
btw i had earlier messed up my system by.. er i put breezy's sources in my sources.list, instead of hoary ](*,) . That cld explain the problem.

Anyways i really need help here
Thanks

---

### Post by dcstar on 2005-11-12
[QUOTE=grizzly]After exploring a bit it turns out all my dependency problems comes down to libc6 not installed to the required version.
```
Depends: libc6 (=2.3.2.ds1-20ubuntu14) but 2.3.5-1ubuntu12 is to be installed
```

Synaptic shows that i have the latest version(2.3.5) of libc6 so there nothing that  i can do  here :( . In other words i am stuck . I have this prob for a few days now, searched everywhere but found no solutions.
..........
Anyways i really need help here
Thanks[/QUOTE]
The line says "=", not ">=" which implies that it needs exactly that old version of libc6.

You may try to "Force" the version to the older one, but whatever you are trying to install is hardly worth the trouble if it is going to have a set dependence on one version of a library.

---

### Post by grizzly on 2005-11-12
I don't think the prob is with the application, many libraries complain and there is whole chain where i library depends on the other . The chain leads to this libc6 thing.
Have a look at my synaptic [Screenshot](http://img215.imageshack.us/img215/4156/shot8an.png) . Can someone compare it theirs? Just search for 'libc6' in synaptic , if you are using hoary

---

### Post by dcstar on 2005-11-12
[QUOTE=grizzly]I don't think the prob is with the application, many libraries complain and there is whole chain where i library depends on the other . The chain leads to this libc6 thing.
Have a look at my synaptic [http://img215.imageshack.us/img215/4156/shot8an.png](http://img215.imageshack.us/img215/4156/shot8an.png) . Can someone compare it theirs? Just search for 'libc6'[/QUOTE]
Looks the same as mine.

---

### Post by grizzly on 2005-11-12
Thanks dcstar, can you do one more thing plz?
Can you install libc6-dev and see if it works for you. I get the  above mentioned error

---

