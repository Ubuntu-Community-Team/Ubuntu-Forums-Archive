---
title: "kernel headers problem: cant make"
date: 2009-04-17
forum: General Help
---

### Post by stim on 2009-04-17
I am trying to compile the latest compat-wireless drivers for my bcm4312 card.  I am having some errors with the compile.

```
root@venus:/home/stim/Desktop/compat-wireless-2009-04-17# make
test: 1: 29: unexpected operator
make -C /lib/modules/2.6.27-11-generic/build M=/home/stim/Desktop/compat-wireless-2009-04-17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2
root@venus:/home/stim/Desktop/compat-wireless-2009-04-17# sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
root@venus:/home/stim/Desktop/compat-wireless-2009-04-17# 

```

What else am I missing?

---

### Post by mswamy78 on 2011-08-02
Hello,
I am facing the same issue. Please reply if you have found any solution for your problem.

Thanks.

---

