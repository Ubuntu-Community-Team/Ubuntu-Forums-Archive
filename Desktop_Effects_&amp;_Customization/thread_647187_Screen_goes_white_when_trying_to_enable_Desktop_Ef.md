---
title: "Screen goes white when trying to enable Desktop Effects"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by CptTenalp on 2007-12-22
Okay, so this is my first time really using Linux, and the first time posting here. I tried to look around on google and around here before making a post about my problem, and I hope that this is the correct place to do so, if not then I am very sorry. Anyway, here goes.

I just got Ubuntu 7.04 installed, and while messing around with stuff I come across the "Desktop Effects", yet when I try to enable it my screen goes white for about half a minute then reverts to normal. I looked around a bit and found out how to track down my graphics card information so I'll include that. If anything else is needed just tell me what it is and how to get it. Many thanks in advance.

  *-display               
       description: VGA compatible controller
       product: 82810 CGC [Chipset Graphics Controller]
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@00:01.0
       version: 03
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: driver=i810_smbus latency=0
       resources: iomemory:f8000000-fbffffff iomemory:f4000000-f407ffff irq:11

---

### Post by Ub1476 on 2007-12-22
Ubuntu 7.10 is the latest version. Why don't you use that?

For the graphic card I'm more used to this way:

```
lspci | grep VGA
```

and for compiz (Effects) error, please post the output of this command:

```
compiz --replace
```

I guess you're just missing drivers for your Intel controller.

---

### Post by CptTenalp on 2007-12-22
I tried to enter that in my terminal and every time I did it would give me the same white screen problem.

---

### Post by CptTenalp on 2007-12-26
I'm sorry if this is against the rules here (I looked but didn't see anything, but I've been known to miss stuff), but I just thought that I might bump this to see if anyone else may have encountered this problem, or have a solution to it. Again, thanks for the time, and sorry if this is against the rules.

---

