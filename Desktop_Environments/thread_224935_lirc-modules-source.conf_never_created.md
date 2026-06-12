---
title: "lirc-modules-source.conf never created"
date: 2006-07-28
forum: Desktop Environments
---

### Post by apanloco on 2006-07-28
trying to get lirc working with my pvr-150.

i run:

sudo dpkg-reconfigure lirc-modules-source

over and over again, but the file "/etc/lirc/lirc-modules-source.conf" is not created like it should. even if i try to compile through dpkg-reconfigure the output is this:

da@brutus:/usr/src/linux$ sudo dpkg-reconfigure lirc-modules-source
Building kernel modules ... (output -> /tmp/lirc-kernel-source.1M7snx)
##############################################
##### Couldn't build LIRC kernel modules #####
##############################################
da@brutus:/usr/src/linux$ sudo cat /tmp/lirc-kernel-source.1M7snx
Makefile:1: /etc/lirc/lirc-modules-source.conf: No such file or directory
make: *** No rule to make target `/etc/lirc/lirc-modules-source.conf'.  Stop.
da@brutus:/usr/src/linux$

please, what am i doing wrong?

/D

---

### Post by apanloco on 2006-07-29
bump (sorry) :-/

---

