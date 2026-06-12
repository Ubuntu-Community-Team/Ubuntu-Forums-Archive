---
title: "Make problem - fsam7440"
date: 2005-12-17
forum: General Help
---

### Post by M4v3R on 2005-12-17
Hello,

I'm having a problem with compilation for fsam7440 package (driver for kill switch in Amilo M7440 Notebook). When I try to make it, the following error(s) occur:

```
root@maver:/home/mav/fsam7440# make
make -C /usr/src/linux-headers-2.6.12-10-686/ SUBDIRS=/home/mav/fsam7440 modules
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/mav/fsam7440/fsam7440.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/mav/fsam7440/fsam7440.o] Error 127
make[1]: *** [_module_/home/mav/fsam7440] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [default] Error 2
```

Any ideas where I got wrong? I've already edited script so it's pointing to /usr/src/linux-headers-2.6.12-10.-686 directory, where kernel headers are located.

---

### Post by chien on 2005-12-17
try 

sudo apt-get install gcc-3.4

export CC=gcc-3.4

make

---

### Post by M4v3R on 2005-12-18
OMG, it worked! Thank you very much!

I have one further question. Everytime I want to activate this module when Ubuntu starts, to type "sudo modprobe fsam7440" and type my password. Is there a way to Ubuntu load this module automatically at start?

---

