---
title: "How to build a gtco USB driver kernel module?"
date: 2009-01-26
forum: Education &amp; Science
---

### Post by p10 on 2009-01-26
I am trying to get a Interwrite Learning Board to work on my Ubuntu 8.10-install. But to make it work the way it should I have to build a gtco USB drive kernel module...

The instructions below came with the install CD, but I am not shure how to do these things. What packages do I need to download? Where is the symbolic link supose to be??

Anyone?

> ================================================================================
Recomended Kernel version to build against >= 2.6.18 

To build the gtco USB driver kernel module, please follow the instructions below.
Building a kernel module should only be performed by a Linux Administrator or 
someone with prior experience building kernel modules.
=================================================================================

1. Download and install any packages that your Distribution requires to build kernel modules.

2. Download the kernel source that matches your currently installed kernel.  Type "uname -r" to display your current kernel version.

2. Make sure that /usr/src/linux is a symbolic link to your current kernel source code's root directory.

3. Type "make"

4. Type "make install" to copy the driver module to the modules directory.


To verify module installation:
==============================

Plug in a supported device and the driver should load.  

To see if the module is loaded type "/sbin/lsmod" and look for "gtco" in the list.

You can see the kernel messages by typing "dmesg | more".

---

