---
title: "libgtk-1.2.so.0 and espxe"
date: 2012-11-04
forum: Gaming &amp; Leisure
---

### Post by mouse- on 2012-11-04
Hey, so I followed[ these]("http://www.psy-q.ch/gaming/linux/epsxe_howto/") espxe installation instructions and downloaded espxe 1.6.0 for linux.  I have a 32-bit system and am running Ubuntu 12.10 {Quantal Quetzal}.  When I tried to start eSPXe, I received this error message:
```
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```
I tried running sudo apt-get libgtk1.2 but this did not return any packages.
I realize that the problem I'm having here is probably pretty simple, but does anyone know what's going on here/have any advice for getting epsxe running?

---

### Post by mouse- on 2012-11-04
I figured out the solution to my problem, and figured I would post it just in case someone else might need to know.  libgtk1.2 is an old release of libgtk, and it can be installed if you add the hardy repositories to your sources.list file like this:
```
deb     http://archive.ubuntu.com/ubuntu/ hardy universe deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
```
then, after running apt-get update, libgtk1.2 should install.

---

