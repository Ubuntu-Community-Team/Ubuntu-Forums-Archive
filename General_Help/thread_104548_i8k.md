---
title: "i8k"
date: 2005-12-16
forum: General Help
---

### Post by AndEat on 2005-12-16
I have trying to get temp monitors working through gkrellm, gnome applets, etc.

ik8 appears to be missing. I can't load the module, i can't force the module to load and checking where I think the module should be it is nowhere to be found.

I can't find it to download either.

Any suggestions to prod me forward?

---

### Post by ape on 2005-12-16
What version of the kernel are you using?  This module (i8k.ko) should live under your /lib/modules/<kernel version>/kernel/drivers/char directory (it's there for me using the 2.6.12-10-686 kernel).  I do have to do a force load on it, but once loaded seems to work fine.

---

### Post by AndEat on 2005-12-18
hmmm. I had checked there,  but i8k was nowhere to be found. I checked again and there it was. :???: 

A step in the right direction.  

thanks

---

