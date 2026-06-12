---
title: "Question:are there any disadvantages to compiling every single thing into the kernel"
date: 2005-12-10
forum: General Help
---

### Post by kakashi on 2005-12-10
hello. i wa just compiling the 2.6.14.3 kernel and founf an option to compile all config as yess
```
make allyesconfig
```
i was wondering does this have any seroius affects on performance and reliability other than having a gigantic kernel image.

---

### Post by cilynx on 2005-12-10
Your kernel is loaded into memory.  It stays there.  If you have everything built into the kernel, then the entire image is going to be in kernel-space memory.  If I understand correctly, this means less kernel-space memory for kernel tasks.

Beyond that, you also run the risk of conflicts.  As a non-kernel-expert, that's about the best I can offer...

---

### Post by kakashi on 2006-02-17
bump.

---

### Post by slux on 2006-02-17
Your kernel image is also going to be quite huge if you're compiling in absolutely everything and will have lots and lots of unnecessary stuff that's loaded all the time.

The main advantage of modules is that you can load and unload drivers and features at will..

---

### Post by queenorych on 2006-02-17
1. Generally modules intialize the hardware on load.  I found this handy for instance with a pvr-250 tv card, that would crap out every now and then.  I reload the modules, and I'm back in business.  The same applies for printers,usb joystics etc.


2. If you want to make a boot disk, larger kernels won't fit.

3.  Each modules loaded in the kernel is more code that could cause system problems.  Not worth taking if you don't need support for a sony non-ide drive made in the early 90's, or support for MFM drives.

---

