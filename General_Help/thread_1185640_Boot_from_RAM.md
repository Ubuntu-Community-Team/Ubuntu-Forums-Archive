---
title: "Boot from RAM"
date: 2009-06-12
forum: General Help
---

### Post by mc6415 on 2009-06-12
Well I have a 9.04 Live CD and I was wondering is there any way to load it to RAM, for example with MEPIS you can boot the live cd from ram by adding the 'toram' line to the end of the boot options. Now I've tried 'toram' and 'copy2ram' to no avail, I was wondering if anyone knew a way I could do this?

---

### Post by LowSky on 2009-06-12
The live CD contains too many files to just run from RAM, that why it isn't built to do that. other distros like Puppy are very samll and can do this with ease, but the Ubuntu Live CD contains way to many packages.

---

### Post by wpshooter on 2009-06-12
> **mc6415 said:**
> Well I have a 9.04 Live CD and I was wondering is there any way to load it to RAM, for example with MEPIS you can boot the live cd from ram by adding the 'toram' line to the end of the boot options. Now I've tried 'toram' and 'copy2ram' to no avail, I was wondering if anyone knew a way I could do this?

I would think you would have to have an awful lot of RAM.

However, I would venture to say that the key components are already being loaded to RAM.

---

### Post by mc6415 on 2009-06-12
Well as the live cd normally loads off of the CD which is 700MB I would imagine it would use maybe 2gb at most, after all the distro I mentioned with MEPIS isn't a cut down distro like puppy for example it is itself a fully featured distro this is what got me wondering about ubuntu.

---

### Post by cleary on 2009-07-01
> **LowSky said:**
> The live CD contains too many files to just run from RAM, that why it isn't built to do that. other distros like Puppy are very samll and can do this with ease, but the Ubuntu Live CD contains way to many packages.

Wrong.
The compressed root filesystem (filesystem.squashfs in ubuntu) can be loaded (still compressed @ ~700MB) into a ramdisk and then mounted, instead of mounting it from the cd drive.

This is how most modern livecd distros do it these days - mepis, sidux etc
It requires enough ram to hold the compressed filesystem, plus some for general operating system use (~300MB should be heaps), which means 1024MB ram should be enough for basic running.

I haven't found a definitive answer whether casper on 9.04 can do it yet though...

---

### Post by cleary on 2009-07-02
I've had a look at the source of casper 1.173 (version in jaunty) -
According to the manpage, toram is a supported parameter, but there is no supporting option handling in scripts/casper script.

Interestingly, there are functions for handling it, but there are issues with calls to a function which in turn calls `du` which is not implemented in the version of klibc being used. I tried changing that to use the busybox du, but it threw and unknown applet message...

If I can get my head around the pieces, I'll try and provide a patch/bugreport.
In the meantime, you could hack in a very inflexible option as per [https://wiki.kubuntu.org/BootToRAM](https://wiki.kubuntu.org/BootToRAM)

---

### Post by cleary on 2010-04-28
fyi, casper 1.236 in lucid has reimplemented the toram cheatcode...

---

