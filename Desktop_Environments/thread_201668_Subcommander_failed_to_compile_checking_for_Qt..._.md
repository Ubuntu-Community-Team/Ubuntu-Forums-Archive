---
title: "Subcommander failed to compile: checking for Qt... no"
date: 2006-06-22
forum: Desktop Environments
---

### Post by lzap on 2006-06-22
I have qt3-mt-dev and libqt4-dev installed, but still:

```
checking for APR... yes
checking for APR-util... yes
checking for boost... yes
checking for subversion... yes
    headers   -I/usr/include/subversion-1
    libraries -L/usr/lib
checking for neon... yes
checking for openssl... yes
checking for berkeley db (include)... yes
checking how to run the C++ preprocessor... g++ -E
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking if --enable-static-qt option is specified... no
checking for Qt... no
configure: error: try setting --with-qt or
```

Tried also: ./configure --prefix=/opt/subcommander --with-qt-dir=/usr/lib/qt3 with no luck. What package to install? Thanks

---

### Post by temcat on 2006-06-22
I hit this error when trying to compile metatheme (btw not only on Ubuntu). Still no solution :-(

---

### Post by oeolartep on 2007-05-04
change

 --with-qt-dir=/usr/lib/qt3

with

--with-qt=/usr/share/qt3

---

