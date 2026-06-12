---
title: "kernel images and installers on DVD"
date: 2007-10-08
forum: Development CD/DVD Image Testing
---

### Post by tkmsr on 2007-10-08
I copied the kernel and initrd from installation DVD of Linux
to my boot folder
#cp DVD-.iso/boot/i386/loader/vmlinuz                           /boot/
#cp DVD-.iso/boot/i386/loader/initrd.gz                           /boot/

and copied the ISO image of  DVD on a partition on hard disk that
was completely free.

 Now I booted from kernel image that was copied by the above commands
then I got the graphical installer screen asking me to start
installation. By this method I have been able to install and test Linux ISO's
 without using CDROM or DVD ROM.

What I want to know is if instead of the kernel image and initrd image
that are on the installation DVD if I put up the kernel image and
initrd that already are existing on a system
i.e.
vmlinuz-2.6.18.2-34-default
and initrd-2.6.18.2-34-default

the system does not begin installation  infact it boots into the new kernel on the system.

My question is what is the difference between the kernel images that
are on the installation media inside DVD-i386.iso/boot/i386/loader/
and the kernel images that are on the system after a fresh
installation has taken place inside /boot/ folder
which was able to boot the system instead of starting installation .

  When a kernel is being downloaded from kernel.org and compiled what parameters do I need to pass to the kernel so that this new kernel is capable of beginning installation on a system that does not have linux previously. 
  How do people at Ubuntu do that when ever a new version comes then a new kernel is there in the installation media how do you put that image and what do you need to compile the kernel to be able to start installaion .Do you people use some tool like Cobbler ,Revisor ,Quemu or Kiwi  to do so or a new spin is released even if some one can tell about the process of release of spin that would be nice.

---

### Post by tkmsr on 2007-10-17
I think I have got a bit of answer the kernel image and initrd that I said on installation DVD is **generic** kernel image which is used for installations
[http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=7](http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=7)
control f with option generic

I need to build a generic CD as image or compile a generic kernel
[http://linuxfromscratch.org/pipermail/lfs-support/2005-February/026055.html](http://linuxfromscratch.org/pipermail/lfs-support/2005-February/026055.html)

---

