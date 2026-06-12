---
title: "About kernel packages"
date: 2006-05-05
forum: Desktop Environments
---

### Post by Cathou on 2006-05-05
Hi,
is there a way to know how a kernel has been built?

e.g:

given the following package:
linux-image-2.6.12-9-k7-smp.deb

.. I would like to know the /usr/src/*/.config that has been used to compile it.

I have retrieved source from Ubuntu repository but I'm confused.
I can't locate this information :sad: 

(newbie)

TIA

---

### Post by insulae on 2006-05-05
you have in /boot the files config-* , meaby you need this.
for example i use the kernel  2.6.15-21-k7 , and i have in boot the config file for this kernel /boot/config-2.6.15-21-k7.
remember, the kernel of ubuntu have many patchs is not the same as the sources of [www.kernel.org](www.kernel.org). but you can use safetly this config file with [www.kernel.org](www.kernel.org) source. if you want you can download the sources and patch sources from the ubuntus repositories

---

### Post by Cathou on 2006-05-05
Thanks, it helped :D

However, the kernel .deb has to be installed first..

I found a solution to look **inside** an arbitrary .deb using **dpkg-deb**.

---

