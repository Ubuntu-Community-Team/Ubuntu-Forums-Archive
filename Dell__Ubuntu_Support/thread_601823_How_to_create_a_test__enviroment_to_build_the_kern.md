---
title: "How to create a test  enviroment to build the kernel of 7.04 on 1420n dells"
date: 2007-11-03
forum: Dell  Ubuntu Support
---

### Post by darodrig on 2007-11-03
HI 

I want to have a src tree of the kernel running on my computer(7.04) to compile and play. So what I did:
1.My version displayed with  uname is 2.6.20-16-generic
2.I downloaded a source kernel tree from kernel.org 2.6.20.16 into my /home/darodrig/linuxsrc/
3.Then I copied all files from the /usr/src/ linux-headers-2.6.20-16-generic/ into my tree and then I tried to compiled and it failed:
root@dell:/home/darodrig/linuxsrc/linux-2.6.20.16# make all
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  CHK     include/linux/compile.h
  SKIPPED include/linux/compile.h
make[1]: *** No rule to make target `arch/i386/kernel/vmi.o', needed by `arch/i386/kernel/built-in.o'.  Stop.
make: *** [arch/i386/kernel] Error 2


So I wanted to know how should I  create the test enviroment and config files so I can have a tree with a kernel equal to the kernel of my laptop 1420n.

Thanks for the help

---

