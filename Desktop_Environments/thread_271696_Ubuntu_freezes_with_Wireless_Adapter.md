---
title: "Ubuntu freezes with Wireless Adapter????"
date: 2006-10-05
forum: Desktop Environments
---

### Post by smadahar on 2006-10-05
[FONT="Arial"]I've had a problem with Ubuntu for months..... here goes:

I have an AMD Athlon 2.4GHz machine, 512MB ram, 250GB hd, ATI Radeon 9200, and a linksys WUSB11v4 wireless adaptor working just fine with NDISWRAPPER and a 2.6.15-27-386 kernel (Dapper).

While running on wireless, the machine will hard-lock-up randomly, but will lock up for sure on compiles, updates and upgrades. Basically I can predict the machine will lock up for sure while I'm attempting a kernel compile. For sure. I have tried everything:

Bios tweaks
Change of RAM
Change of Hard Drive
Change of Graphics adaptors (7 of them from various friends!)
Patching the kernel
adding the mem=nopentium to grub

So far, the only thing that has stopped the freezes is switching from wireless to LAN connection to the internet. Great you say, execpt the computer is supposed to 1 floor up from my router. Therefore wireless is a must, but not if it's going to freeze everytime I do something interesting on the darn machine. Any help (and I mean any) will be gladly recieved. 

Very frustrated.... but full of hope for the experts out there and the wisdom you have....[/FONT]

---

### Post by plowna on 2006-10-07
Just wanted to say I have a very similar problem.

Am running 6.06 Ubuntu with the 2.6.15-27-686 kernel.

As far as I can tell, the random crashes seem to occur from using ndiswrapper to enable my wireless USB card (sis163u based). Unfortunately everything I've tried in order to compile a "new" version of ndiswrapper appears to simply fail to configure the USB wireless properly. (maybe its something I didn't do correctly) I'm also mystified by ndiswrapper's versioning; the "latest" is version 1.25, yet the version returned by the latest packages from ubuntu is 1.8. There's no explanation anywhere that I've seen for this mix of versions.

I removed the ndiswrapper (rmmod) and left it for a day and it ran fine. modprobed ndiswrapper and within an hour, hard lock.

Currently looking to recompile the entire kernel from vanilla sources ... maybe I'll post again next week to see how far I've gotten in making my ubuntu system more stable.

In the meantime though, back to Windows ...

---

