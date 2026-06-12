---
title: "Choosing not to install unnecessary kernel modules"
date: 2005-10-31
forum: Desktop Environments
---

### Post by icekin on 2005-10-31
During install, I get a screen which says "the following kernel modules were automatically detected as being needed for your computer" Then there is a list of kernel modules.

All the modules are listed without explanation. Where can I find a list of these modules and what each expression stands for? For example, atiix is ATI Chipset, sis... is SIS chipset and so on.

My laptop only uses a ATI Rage, so will it be safe if I disable the unnecessary modules (for which I will need the list first)? Do I have to recomplile kernel after doing this? Some people tell me that linux anyways only loads modules which are needed at startup, so installing extra modules won't hurt performance. But I will never be changing my hardware anyway, so I would like to remove all other kernel modules besides the ones that are being used.

---

### Post by RAOF on 2005-10-31
Um, it's probably not a good idea, unless you **really** need the couple of megs of hdd space killing the modules will bring you.  

But you could get the list of loaded kernel modules by running "lsmod".  If you've got everything you're ever going to plug in to your laptop plugged in first, this will **probably** be the maximal set of kernel modules you need.

But really, there is **so little point**.  And what if you later buy a new usb dongle thing, and it won't work because you deleted the kernel module for it?

Oh, and this is **in no way guaranteed to be safe**.

---

### Post by icekin on 2005-11-01
What you say makes sense, so I won't disable anything. Anyway, I ran "lsmod" and I get a lost of all the modules with size and a column that says "used by" Some entries have something next to the used by like "serial_cs" :

Line : "pcmcia - 24584 - 6 - serial_cs,xirc2ps_cs"

I suppose that if the used by number is 0, then no other module or whatever is using it. Also, the modules are still listed as expressions like udf, serial_cs xirc2ps_cs and so on. How do I know what these stand for? I could google up each one individually, but I was wondering if anyone already has a list of the modules and what they stand for. I googled that up, came up with nothing useful. Even kernel.org doesn't seem to have it.

---

### Post by RAOF on 2005-11-01
All of the modules listed by lsmod are being used - the "used by" column gives the module dependencies (ie: what modules are loaded because **other modules** need them).

As for a list of what modulenames correspond to what devices/subsystems... I don't know of any.  I suspect that the developers feel that anyone who wants to get involved with the nitty-gritty of kernel modules can probably guess what the names mean anyway, or don't care.  Some of the names are really technical - for example, I've got the module "saa7134" loaded.  The saa7134 is  the driver for a chip (the tuner, I think) on my tv-tuner card.  So it's not even the case that 1 module corresponds to 1 device.

---

