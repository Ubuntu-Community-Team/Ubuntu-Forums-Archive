---
title: "toshiba satellite m45-s165"
date: 2005-12-28
forum: General Help
---

### Post by louis_nichols on 2005-12-28
hi everybody! here's my problem.

A friend of mine has the laptop in the subject and I suggested ubuntu vs Win XP. Now, I would like to demonstrate a little, using the livecd but I ran into a small problem. First, I tried to boot the livecd and it stopped ith a black screen. Then I tried booting with acpi=off vga=771 and worked fine up to a point.
It wasn't able to configure Xorg. It says it can't find the driver for the specific graphics chipset. Now, the machine has a ubuntu ati radeon xpress 200m.

any idea f a workaround, so my friend can see ubuntu on her laptop before installing?

thx

---

### Post by body-snatch-her on 2005-12-28
I have a Toshiba L25-s119 which also uses ati x200m chipset and XP also. I would assume your problem has something to do with the fact that the chipset may not (yet) be supported by *NIX, at least w/out some serious fiddling around.
 I can suggest an alternative for demonstration purposes which also happens to be how I am currently running Ubuntu. You can go to [www.vmware.com](www.vmware.com) and download the free VMware player and a preconfigured Ubuntu installation VM to run within the player (called Browser App VM /or BAVM). It was designed to run as a web-safe way to surf, try out VMware, and check out Ubunto along the way. While there are apparently some VMware specific kernel tweaks (the doc's caution against updating the build), it is otherwise a fairly complete distro. It runs fairly well on my machine (Celeron M 370 with 1.25 MB ram, XP home SP2) using a 256 MB VM size, so I would guess it would run OK as long as you have at least 512 MB physical system memory. I am using VMnet0 (bridging) behind a hardware firewall to share the WiFi-g hardware using seperate router supplied IP addresses (XP vs. VM), but you can set it up several ways to suit your needs.
 Going this route would provide your friend a way to explore Ubuntu while running XP at the same time and if it was determined that XP is not desireable, then perhaps by that time the chipset issues will have be resolved so you can do a good install over XP, or whatever.

---

