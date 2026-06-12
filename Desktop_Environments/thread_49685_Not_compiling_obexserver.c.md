---
title: "Not compiling obexserver.c"
date: 2005-07-17
forum: Desktop Environments
---

### Post by KriC on 2005-07-17
hi everyone,
i'm just trying to make my BT/USB works and i found lots of how-to on internet and all of 'em say that i have to compile a file called obexserver.c in the src directory  of openobex-apps in this way:

cc -o obexserver obexserver.c libmisc.a -lopenobex

now my problems are two:
1) i don't have (and i don't know how) a library called libmisc.a, i tryied to download that somewhere on internet, but still say that my kubuntu can't find that, i moved this file, libmisc.a, on the directory src of openobex-apps and my computer see it, 
2) but after i type the command line above it returns this:

/tmp/ccAbAUlK.o(.text+0x1c): In function `main':
: undefined reference to `obex_event'
collect2: ld returned 1 exit status

if someone read this post, please answer me, i don't really know what to do

thankz a lot guys


KriC

---

### Post by Feanor on 2005-07-17
I've bluetooth and it works fine. I take obexserver from apt-get so try to do

```
sudo aptitude install obexserver
```

i suggest to install also bluez-utils and if you are under KDE kdebluetooth framework

---

### Post by KriC on 2005-07-17
Thank you so much
everything are working now
i never knew that there was a program called kdebluetooth framework
it would semplifyied my life time ago

thanks again


KriC

---

### Post by ltmon on 2005-07-18
kdebluetooth is not in the normal repository, but you can use the instructions at [https://www.ubuntulinux.org/wiki/SimoneGotti](https://www.ubuntulinux.org/wiki/SimoneGotti) to get a precompiled package of kdebluetooth.

It works like a charm with my SEk700i and my girlfriends nokia.

L.

---

