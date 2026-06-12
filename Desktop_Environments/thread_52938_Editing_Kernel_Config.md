---
title: "Editing Kernel Config"
date: 2005-07-29
forum: Desktop Environments
---

### Post by matva on 2005-07-29
I'm trying to get the i8k kernel module to run automatically, and have read that i need to edit my kernel config in order to do this. it involves changing an "m" to a "y". I have found a kernel config in a boot folder, but it won't let me edit it. I'm guessing the actual file i need to edit is located somewhere else?

I'm doing all this in order to run i8kfan, a fan controller for inspiron dell laptops.

thx

---

### Post by Xian on 2005-07-29
It probably won't let you since it requires admin priviledges. However, any time that you modify your kernel config, you must then compile a new kernel so those modifications will take effect. This is usually done with the make menuconfig command which is issued during the kernel building process.

For more info see [Kernel Compile How-To](https://wiki.ubuntu.com/KernelCompileHowto).

---

### Post by az on 2005-07-29
Changing the kernel config file will not change anything on your system without using the modified file to configure another kernel and compile it.  The you have to install it and boot from it.

However, the "m" in the config means that it is a module.  A module is a kernel configuration that you can load.  It can work 100% without being part of the kernel at boot time.  You load it when you need it.

Check to see if it is already loaded

lsmod


if it is not, find the name of the module and load it

sudo modprobe ik8fan

No need to change your kernel.

To get the module to load at boot time, insert the name of the module with the other ones in /etc/modules.


sudo gedit /etc/modules

---

### Post by saliboy on 2005-09-01
Hi,

Can someone help me to set up i8kfan controller on my Dell Latitude C800. I have downloaded utilities but don't know what to do next?

Sasha

---

