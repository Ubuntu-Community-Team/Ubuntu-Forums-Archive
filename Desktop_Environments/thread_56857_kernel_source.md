---
title: "kernel source"
date: 2005-08-14
forum: Desktop Environments
---

### Post by frenchie on 2005-08-14
Hi everyone. I'm in kind of a rush so any help would be appreciated. I'm trying to get all of my drivers and software to work before i upgrade the kernel. Could anyone please point me to the place were i can get the stock Kububtu kernel? Thanks in advance :)

---

### Post by az on 2005-08-14
install the linux-tree package

kurn@ubuntu:~$ apt-cache search linux-tree
linux-tree-2.6.10 - Linux kernel tree for building prepackaged Ubuntu kernel images
linux-tree - Linux kernel tree for building prepackaged Ubuntu kernel images


If you need to build drivers for the stock kernel, install the linux-headers package.  That is all you need to build drivers.  You will have to work harder to use the linux tree package for that.

---

