---
title: "Strange libc6 errors!! System not working properly"
date: 2006-03-24
forum: Desktop Environments
---

### Post by ispmarin on 2006-03-24
Hello everybody. I was playing with some sdl libraries from dapper on my breezy system. Installed some, but when asked to install libc6, i said no (no stomach for that). Everything kept working fine, but then some things stopped working, like opera static compiled and open office2. When tried to reinstall libc6, got this error:
+++++++++++++++++++++++++++
These libraries were found in /usr/lib:
libpthread.so.0

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: erro processando /var/cache/apt/archives/libc6_2.3.5-1ubuntu12.5.10.1_amd64.deb (--unpack):
+++++++++++++++++++++++++++++
If this library is removed by hand and reinstalled, the libc6 works, but the problem continues, and when you try to install new software the error appears again. What is messing up with that? Even ldd does not work!!

---

### Post by ispmarin on 2006-03-24
this is the error from ldd:
+++++++++++++++++++++++
/usr/bin/ldd: line 171: /lib/ld-linux.so.2: Arquivo ou diretório não encontrado
ldd: /lib/ld-linux.so.2 exited with unknown exit code (127)
+++++++++++++++++++++++
File or directory not found!!

What is happening? This is beginning to scare me...

---

