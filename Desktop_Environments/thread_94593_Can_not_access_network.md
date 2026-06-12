---
title: "Can not access network"
date: 2005-11-24
forum: Desktop Environments
---

### Post by jettana on 2005-11-24
Hello all,

I am a newbie and I am trying to install RTAI 3.2. I use Ubuntu.

First I patch hal-linux-2.6.10-i386-r9.patch to kernel 2.6.10
then config and compile the kernel.It seems all ok and then
I install it.After reboot it detect network for long time ,so can
not use network and can not use usb mouse because driver
(usbhid) not load.

I use this :
   Intel(R) Pentium(R) 4 CPU 2.40GHz
   gcc (GCC) 3.3.5
   kernel 2.6.10
   rtai 3.2
   RealTek RTL8139

I do this step for install rtai 3.2:
1.apt-get install linux-tree-2.6.10
2.cd /usr/src
3.tar xvfj linux-source-2.6.10.tar.bz2
4.cd linux-source-2.6.10
5.cp /boot/config-2.6.10-5-386 .config
6.make oldconfig
7.make menuconfig
    *  "Adeos" is selected (Adeos Support -> Adeos Support)
    * "Loadable module support -> Module versioning support" is disabled
    * "Kernel hacking -> Compile the kernel with frame pointers" is disabled
    * "Processor type and features -> Use register arguments" is disabled 
(CONFIG_REGPARM)
8.make-kpkg clean
9.make-kpkg --stem linux --initrd --append-to-version=-rtai3.2 kernel_image
10.dpkg -i ../linux-image-2.6.10-rtai3.2_10.00.Custom_i386.deb
11.reboot

What can I do now?

Thank you.
Jettana Mutchakwnag

---

