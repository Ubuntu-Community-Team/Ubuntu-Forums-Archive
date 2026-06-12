---
title: "Rebuild Ubuntu Kernel"
date: 2005-12-28
forum: General Help
---

### Post by Tiry on 2005-12-28
Hi,

The stock 2.6.12 prebuild ubuntu kernel works fine on my asus laptop.

I try to rebuild this ubuntu kernel from the sources.
My purpous is to be able to rebuild the kernel from source in ordrer to be able , later, to do a specific kernel including suspend2 patches.

I use gcc 3.4 and make-kpkg with a .config that is a copy of the stock config-2.6.12.
The build runs fine and the rebuilt kernel boots but :
 - the framebuffer is gone : so I have a black screen during boot
   ( but the framebuffer is enable in my .config )
 - the ipw2200 wifi card is not found any more (no eth1)
   ( but the ipw2200 kernel module is included in my .config)

So, here is my question :
What do I have to do to be able to rebuild from the source the same kernel as the prebuilt one shipped with breezy ????

Thx,


Tiry

---

### Post by TrinitronX on 2005-12-29
Instead of using the vanilla kernel source from kernel.org, try using the customized ubuntu version instead.  There's a package you can get from synaptic called "linux-source-2.6.12", Description:"Linux kernel source for version 2.6.12 with Ubuntu patches"
I compiled my kernel with this, and have had no problems (I also manually configured it to support some processor specific options for my P4 with HyperThreading, as well as AGP support in the kernel, for use with my fglrx ATI drivers).  For a guide on how to do this, see the wiki here: [https://wiki.ubuntu.com/KernelBuildpackageHowto](https://wiki.ubuntu.com/KernelBuildpackageHowto)

---

### Post by Tiry on 2006-01-02
Hi,

Yes I used linux-source-2.6.12 from ubuntu package.
But the kernel I build is still not the same as ubuntu pre-build kernel ...

Any idea ?


Tiry

---

