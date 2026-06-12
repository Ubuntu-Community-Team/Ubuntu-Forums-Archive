---
title: "can't compile bX IRC client under intrepid"
date: 2009-01-07
forum: General Help
---

### Post by Neuroshock on 2009-01-07
Hello everyone,

I am trying to compile ircii-pana-1.1-final under Intrepid. The *./configure* command works perfectly but I get the following error when I type *make* and *make install*:

```
In function ‘open’,
    inlined from ‘create_ipc_socket’ at commands2.c:2578:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
gmake[1]: *** [commands2.o] Error 1
gmake[1]: Leaving directory `/root/BitchX/source'
make: *** [BitchX] Error 2

```

Anyone can help? It would really be appreciated.

---

### Post by Titan8990 on 2009-01-07
Do you have all the proper libraries needed to compile? It usually says in a README or INSTALL file in the source directory which dependencies are needed.

---

### Post by phisher1 on 2009-01-07
Do you have build-essential and libncurses5-dev installed?

---

### Post by euxenos on 2009-02-03
In function ‘open’,
    inlined from ‘create_ipc_socket’ at commands2.c:2578:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [commands2.o] Error 1
make[1]: Leaving directory `/home/euxenos/BitchX/source'
make: *** [BitchX] Error 2
euxenos@jin:~/BitchX$ sudo apt-get install libncurses5-dev
[sudo] password for euxenos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
euxenos@jin:~/BitchX$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by destiney on 2009-03-25
Same issue.  Been compiling this same package for years without issues, now it fails on Ubuntu 8.10:

commands2.c:2666: warning: value computed is not used
In function ‘open’,
    inlined from ‘create_ipc_socket’ at commands2.c:2578:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [commands2.o] Error 1
make[1]: Leaving directory `/usr/src/BitchX/source'
make: *** [BitchX] Error 2

---

### Post by destiney on 2009-04-07
> **destiney said:**
> Same issue.  Been compiling this same package for years without issues, now it fails on Ubuntu 8.10:

commands2.c:2666: warning: value computed is not used
In function ‘open’,
    inlined from ‘create_ipc_socket’ at commands2.c:2578:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [commands2.o] Error 1
make[1]: Leaving directory `/usr/src/BitchX/source'
make: *** [BitchX] Error 2


Anyone?  Still waiting..

---

### Post by andrew.46 on 2009-04-26
Hi,

It is probably not what you want to hear but I note that my 'other' distro has only just [removed BitchX from the distro]("http://www.slackware.com/security/viewer.php?l=slackware-security&y=2009&m=slackware-security.285737") today:

> 
This is a notice that bitchx, an IRC client based on ircii-EPIC4, has been
removed from Slackware -current and will not be part of future Slackware
releases.  Security issues and bugs have been reported, but upstream
work seems to have stalled leaving bitchx in a state where there are
known problems without official (or in some cases any) fixes.

The most secure course of action is to remove bitchx from the system and
switch to using a supported IRC client.


Still want to install this one?

Andrew

---

