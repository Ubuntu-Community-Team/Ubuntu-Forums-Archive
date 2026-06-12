---
title: "python-gmenu Configuration error"
date: 2011-07-02
forum: Desktop Environments
---

### Post by devstuff on 2011-07-02
Hey all,

I am having issues after a distro update when trying to install python-gmenu.

The line "eval: 1: 8:[1: not found" actually outputs a non displayable character.

Help would be very much appreciated.. :)

Reading package lists... Done


Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
/bin/sh: /usr/sbin/dpkg-preconfigure: not found
Setting up python-gmenu (2.30.5-0ubuntu3) ...
eval: 1: 8:[1: not found
dpkg: error processing python-gmenu (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 python-gmenu
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by devstuff on 2011-07-02
If this helps :-


lrwxrwxrwx 1 root root 9 2011-07-02 20:37 python -> python2.6

---

