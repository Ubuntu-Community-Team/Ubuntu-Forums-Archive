---
title: "need graphics help on new PC build"
date: 2009-04-05
forum: General Help
---

### Post by razy60 on 2009-04-05
I have just put together a new PC,using the following parts.
Asrock ALiveNF6G-GLAN mobo
AMD Athlon x2 7750 black edition
4Gb kingston xps highspeed ram
250Gb Sata drive.
The board uses Nvidia geforce 6150SE/nforce 430 chipset.
The PC is connected to my TV using a VGA cable(
I have tried the live cd on this system but the graphics are lousy, i had a similar problem with my old pc. On my laptop and various other PC's the graphics work fine straight from the cd. (not tried 8.04 this worked fine as live then as an install on my old system).
What i dont want to do is install 8.10 only to come up against a huge amount of problems again, or go out and buy a decent graphics card only to find that the drivers dont work again.
Any one got any tips tricks or advice before i try the install?
The system is running windows7 fine, so there are no known hardware problems to consider.(this just a temporary os until i can get ubuntu to run correctly)

Cheers for any help

Raz

---

### Post by atomizer on 2009-04-05
the nvidia drivers should work for you. you can install them after you installed ubuntu.

Shouldn't you use a 64-bit ubuntu to make use of your 4 Gig memory? I thought you can only use 3Gig (and a bit) on a 32-bit OS

---

### Post by razy60 on 2009-04-05
> **atomizer said:**
> the nvidia drivers should work for you. you can install them after you installed ubuntu.

Shouldn't you use a 64-bit ubuntu to make use of your 4 Gig memory? I thought you can only use 3Gig (and a bit) on a 32-bit OS

Yes your right about the memory, but as the board uses dual channel i had to get 2x2GB sticks to get the benefit also i am still not convinced that 64bit is supported enough(i had not realy considered it though, so thanks for the reminder)

As for the drivers my main bone of contention is that whenever i have tried a live CD i get the correct resolution straight on other PC's so why not this one.

Cheers 

Raz

---

### Post by coffeecat on 2009-04-05
When you run a live CD with a nvidia graphics card, it runs with the open-source 'nv' driver. In my experience the image isn't quite as sharp as with the proprietary 'nvidia' drvier (and, of course, you don't get hardware acccceleration), but I wouldn't call it 'lousy'. On my system with a 24" monitor, I got the correct 1920x1200 resolution running the live Intrepid CD with the 'nv' driver. And with the Hardy CD iirc. 

So what resolution did you get, and with what sort of monitor? Some monitors don't put out good edid data and this confuses the xserver, so the problem may be with the monitor.

Anyway, I know way of testing the proprietary 'nvidia' driver before you install. You have to do a reboot before the driver can be activated, so clearly you can't do this when running live.

**Edit:** sorry, missed the bit about the TV. When I tried hooking a PC up to my TV the image was, indeed, 'lousy'. I had to go into the TV menu and do an autoconfig, and then it was OK. This was because of a discrepancy between the TV pixel resolution [noparse](something like 1366x768), and the graphics card/driver output (something like 1360x768). [/noparse]So much for industry standards. :roll:

---

