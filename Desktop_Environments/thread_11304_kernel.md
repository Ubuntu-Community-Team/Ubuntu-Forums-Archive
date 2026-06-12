---
title: "kernel"
date: 2005-01-15
forum: Desktop Environments
---

### Post by pavkonti on 2005-01-15
I have amd thunderbird 900Mhz. which kernel should I use 386 or 686?

---

### Post by feneks on 2005-01-16
kernel-image 386 basicaly supports all CPUs of Intel/ AMD/ VIA  (=Intelcompatible CPUs)

586 are kernels for Intel's Pentium (MMX) and higher
686 are kernels for Intel's PII / PIII / PIV

AMD Athlon Thunderbird 900Mhz is a Prozessor of AMDs seventh generation. Shortcut is K7 and this is what you should look for. 
```
sudo apt-get install kernel-image-2.6-k7
```

Ubuntu will keep the kernel-image-386 but it won't be automaticaly booted by GRUB. GRUB will use the new kernel-image as standard. Keep the basical image because this one will support you Processor for sure. Though not all abilities of the processor will be supported when you use this old image.

--edit--
nice ears  :mrgreen:

---

### Post by az on 2005-01-16
Please say if you see any change in system performance.  I beleive the improvements are only minimal, if not imperceptible.

---

### Post by pavkonti on 2005-01-16
it is faster :). There is a difference with pages with flash animations, it is better :)

---

### Post by feneks on 2005-01-16
VICTORY!!!

I think it's a good idea to use an adjusted kernel because then you have support for all commands, the CPU knows. Just an example. If you have an Pentium MMX and you use the 386-kernel you won't be able to use MMX because 386 supports 486 CPUs too. These have no idea of MMX so it isn't included. I coud be wrong but this is how I understod this topic.

---

