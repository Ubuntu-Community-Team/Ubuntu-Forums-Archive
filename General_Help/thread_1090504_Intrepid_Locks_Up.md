---
title: "Intrepid Locks Up"
date: 2009-03-08
forum: General Help
---

### Post by nova47 on 2009-03-08
I've got Ubuntu running on a computer I've built and I literally can't keep it running for more than 5 minutes before it locks up. No keyboard, no mouse, no nothing. I'm using the following hardware:

OCZ OCZ3P20004GK DDR3 2000MHz 4 GB
Intel Core 2 Duo E8500 Dual-Core Processor, 3.16 GHz, 6M L2 Cache, 1333MHz FSB, LGA775
EVGA 132-YW-E180-A1 nForce 790i SLI FTW Digital PWM Motherboard
Two EVGA 512-P3-N871-AR GeForce 9800GTX 512MB DDR3 PCI-E 2.0 Graphics Card (run in SLI)

I'm running Ubuntu Intrepid 8.10 32 bit. I was wondering if anyone happens to know of any fixes.

---

### Post by nova47 on 2009-03-11
Found the problem but haven't come up with a solution yet. I tried taking out my wireless card and suddenly all the crashes went away and I was able to run Ubuntu flawlessly. Put it back in and immediately the crashes started up again. I've got a WMP110 Rangeplus so if you're encountering problems I'd check that out. I'll write back if I come up with a solution.

---

### Post by LowSky on 2009-03-11
Sounds like a bad wifi card or bad PCI slot. Even if the card doesn't work it shouldn't cause lockups.

---

### Post by nova47 on 2009-03-15
Card works fine in Windows and in the other computer I tried it on. The only place I have a problem with it is Ubuntu.

---

### Post by Slim Odds on 2009-03-15
> **nova47 said:**
> I'm running Ubuntu Intrepid 8.10 32 bit. I was wondering if anyone happens to know of any fixes.

Well... for starters... with that hardware you should really run the x86_64 version of Ubuntu. Otherwise, you won't even get to use all of that 4G of RAM.

---

### Post by nova47 on 2009-03-17
lol I could but most everyone else uses 32 bit so it's a lot easier to find fixes to problems with 32 bit (not to mention you don't run into all those problems with apps not meant for 64 bit ints). Plus I can't even fathom a reason I would actually need to use 4 gigs of ram in Ubuntu.

---

