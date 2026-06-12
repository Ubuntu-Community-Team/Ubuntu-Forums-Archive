---
title: "need to find linux source for cdemu"
date: 2005-09-27
forum: Desktop Environments
---

### Post by ginronin on 2005-09-27
I have been try to install CDemu in Kubuntu but i think it needs to know where the linux source is. this is what happens when use 'make'

/home/ginronin/Setups/cdemu-0.7/cdemu_kernel.h:90: error: storage size of `info'                                                          isn't known
/home/ginronin/Setups/cdemu-0.7/cdemu.c:281: warning: `cdemu_request' defined bu                                                         t not used
make[2]: *** [/home/ginronin/Setups/cdemu-0.7/cdemu.o] Error 1
make[1]: *** [_module_/home/ginronin/Setups/cdemu-0.7] Error 2
make[1]: Leaving directory /home/ginronin/Setups/cdemu-0.7/cdemu_kernel.h:90: error: storage size of `info'                                                          isn't known
/home/ginronin/Setups/cdemu-0.7/cdemu.c:281: warning: `cdemu_request' defined bu                                                         t not used
make[2]: *** [/home/ginronin/Setups/cdemu-0.7/cdemu.o] Error 1
make[1]: *** [_module_/home/ginronin/Setups/cdemu-0.7] Error 2
make[1]: Leaving directory `/usr/src/linux'
make: *** [all] Error 2

make: *** [all] Error 2

i have tried downloading the linux source and putting it in     /usr/src/linux but it still gives this error. do any of u guys know if there is a guide to installing it or better yet is there package? thanks for any help 

oh yea i check kynaptic for a package.

---

### Post by frodon on 2005-09-27
I installed cdemu following the guide in [cdemu]("http://cdemu.sourceforge.net/") website. All works without any problems.
Are you sure that you have well installed your linux sources ?

EDIT : EjeCt have posted a [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=69530") about cdemu today.

---

