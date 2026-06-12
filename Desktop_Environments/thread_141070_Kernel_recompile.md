---
title: "Kernel recompile"
date: 2006-03-07
forum: Desktop Environments
---

### Post by holobyted on 2006-03-07
Been recompiling my kernel lately to get the most out of my system and so far, so good... but I'm still not sure about the following:

I know I should select Athlon64 as my architecture, since I use an A64 3200+ - but after reading up on all the x64 issues and the like, I'm kind of scared to do it :p


Would recompiling the kernel as x64 bring forth all those problems, or is it a different story altogether?


Thanks, sorry for the noob question :p

---

### Post by colo on 2006-03-07
This setting only adapts the Makefile to issue a different -march to gcc, which is compiling the kernel binary. The problem's you've read about most probably relate to running a true 64bit-system, and NOT a 32bit-kernel finetuned to make use of your CPU's extra IA-32 execution units.

It's completely safe to change that setting so it fits your CPU.

---

### Post by holobyted on 2006-03-07
Awesome. I would, however, need the 64-bit version of the official nVidia drivers, right?

---

