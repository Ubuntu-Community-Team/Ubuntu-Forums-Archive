---
title: "xps 1530 enable PAE"
date: 2008-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tCarls on 2008-10-15
I recently got a Dell XPS 1530 with Ubuntu. I noticed that the kernel doesn't enable PAE so it only sees 3.5G of memory instead of the full 4G. I'm wondering what the best way to see the full memory would be. Does anyone have any experience getting this working?

I tried downloading the kernel source and recompiling with PAE enabled. It worked and I can now see the full 4G, but now I'm having problems with some of the proprietary drivers. I'd rather not go through the trouble of compiling drivers and keeping up to date outside of synaptic.

I've thought about installing the ubuntu-server kernel, but that has a few options I don't like (like disabling preemption.)

I guess the last option would be to install 64-bit Ubuntu. This seems to be the best option but I've had some trouble with things like flash in firefox on previous 64-bit machines, so I'm a little hesitant about this as well.

What would you recommend?

---

### Post by adaptr on 2008-10-15
Due to the way the IBM AT architecture works (yes, this is what your PC uses), every 32-bit OS will lose the top X MB of RAM to I/O slots and PCI / PCIe device space, which must be mapped into the physical 4GB to enable the CPU to use these devices.
512 ~768 MB is common, leaving you with 3.25 ~3.5 GB of usable RAM.

The only real solution is to use a 64-bit OS, which can address terabytes of physical memory.

---

### Post by jespdj on 2008-10-16
> **tCarls said:**
> I guess the last option would be to install 64-bit Ubuntu. This seems to be the best option but I've had some trouble with things like flash in firefox on previous 64-bit machines, so I'm a little hesitant about this as well.

What would you recommend?
Install 64-bit. Installing Adobe Flash is not as difficult as you think. In fact, it is exactly the same as on 32-bit Ubuntu; you install the package flashplugin-nonfree and you're done. On 64-bit Ubuntu, this will automatically install nspluginwrapper, to make the 32-bit Flash plugin work in 64-bit Firefox.

---

### Post by s0cket on 2008-10-19
> **adaptr said:**
> Due to the way the IBM AT architecture works (yes, this is what your PC uses), every 32-bit OS will lose the top X MB of RAM to I/O slots and PCI / PCIe device space, which must be mapped into the physical 4GB to enable the CPU to use these devices.
512 ~768 MB is common, leaving you with 3.25 ~3.5 GB of usable RAM.

The only real solution is to use a 64-bit OS, which can address terabytes of physical memory.

That has little to do with IBM AT and more to do with IA-32.  I do wish Ubuntu would compile their kernels with 64 GB PAE support.  I have the same problem... I'm restricted to 32bit for a handful of non-specific reasons at work.  But my work system has 8 GB of system memory.  I also have an Nvidia card which makes matters worse... blah.  It's all easy to fix but not worth my time.. I just deal with my 3.5 GB of memory.

---

### Post by jespdj on 2008-10-20
> **s0cket said:**
> That has little to do with IBM AT and more to do with IA-32.  I do wish Ubuntu would compile their kernels with 64 GB PAE support.  I have the same problem... I'm restricted to 32bit for a handful of non-specific reasons at work.  But my work system has 8 GB of system memory.  I also have an Nvidia card which makes matters worse... blah.  It's all easy to fix but not worth my time.. I just deal with my 3.5 GB of memory.
The kernel of Ubuntu Server is compiled with PAE support.

I don't know what your "non-specific reasons" are to stay with 32-bit, but you should check if those reasons are actually valid. Do you know that 32-bit software also runs on 64-bit Ubuntu? And there's a tool called [getlibs](http://ubuntuforums.org/showthread.php?t=474790) to automatically install the necessary 32-bit libraries.

And why does an nVidia card make matters worse? nVidia cards work the same on 32-bit as on 64-bit Ubuntu, the same drivers are available for both 32-bit and 64-bit. The nVidia 8600M GT in my XPS M1530 works fine on 64-bit Ubuntu 8.04.

---

