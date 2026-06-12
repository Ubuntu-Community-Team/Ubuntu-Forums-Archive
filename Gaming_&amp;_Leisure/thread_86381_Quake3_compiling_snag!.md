---
title: "Quake3 compiling snag!"
date: 2005-11-05
forum: Gaming &amp; Leisure
---

### Post by CheapAlert on 2005-11-05
For some reason, i've hit a snag that I and my quake buddies have no clue what's going on. Most say it's nasm not being installed, but it is installed (apt-gett'd)

Attempted but still failed:
- reinstalling nasm
- chmodding all folders and files to 777 
- chmodding ./unix/cons to +x
- compiling other q3 engine distros like nxabega 
- running with sudo
- running with sudo su -p

```

cs@c950ubuntu:~/oasrc/quake3-1.32b/code$ sudo cons -- gcc=gcc-2.95 g++=g++-2.95
sh: /lib/libc.so.6: Permission denied
GCC version: 2.95.4 - i386-linux
cpu : x86
OS : Linux
libc:
configured for debug build
CFLAGS: -pipe -fsigned-char -g -Wall -Werror -O
cons: error in file "unix/Conscript-dedicated" (don't know how to construct debug-x86-Linux-/core/dedicated/unix/ftol.o from debug-x86-Linux-/core/dedicated/unix/ftol.nasm.)
cons: error in file "unix/Conscript-client" (don't know how to construct debug-x86-Linux-/core/client/unix/ftol.o from debug-x86-Linux-/core/client/unix/ftol.nasm.)
cons: error in file "unix/Conscript-client" (don't know how to construct debug-x86-Linux-/core/client-smp/unix/ftol.o from debug-x86-Linux-/core/client-smp/unix/ftol.nasm.)
cons: script errors encountered: construction aborted
```

Also on a clean unpacking of fresh q3a source, it just simply says "access denied" whenever i try to ./unix/cons. I'm really supposed to use ./unix/cons instead of just cons really.

If anyone wants to try to figure this all out out, here's the [Q3A 1.32b source](http://www.planetgargoyle.com/openarena/quake3-1.32b.zip) licensed under the GNU GPL.

---

### Post by pmjdebruijn on 2005-11-21
Hi,

Try using the icculus.org sources:
[http://www.icculus.org/quake3/](http://www.icculus.org/quake3/)

Or try one of my precompiled binaries for Ubuntu:
[http://www.xs4all.nl/~bruijn9/quake3/](http://www.xs4all.nl/~bruijn9/quake3/)

Good luck,
Pascal de Bruijn

---

