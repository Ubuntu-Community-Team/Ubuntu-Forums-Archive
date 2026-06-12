---
title: "Dell XPS m1710"
date: 2007-07-03
forum: Dell  Ubuntu Support
---

### Post by CorranSW on 2007-07-03
Hi i was trying to install Ubuntu on my laptop a month or two back... And i tryed again recently... For some reason the Dell XPS m1710 doesent seem to want me to install ubuntu on it.. I have installed Ubuntu on several desktops before and i havent seen any problems like this...  Ill start by steps... I went to my laptop bios... Switched the boot order to allow the CD drive to boot first... Inserted Ubuntu 6.10 CD and restarted.... Then ubuntu boots off the live CD when i restart... I click install... Everything goes smoothely untill i get to the partitioning section... I setup my partition size and start the resizing.... It says it is working when there is no progress being made partitioning my hard drive..  I leave it for a couple hours.. Come back... Still no progress has been made.. K so i try again... Same problem... And i try again the next day after working through some things i thought would be the problem... Still the problem persists me...  
Has anyone encountered this on the XPS m1710 laptop system????
Any help is appreciated...

---

### Post by dmarsh on 2007-07-03
No problems with my system installing the Feisty Fawn release- I've had the laptop for about a month, and Ubuntu went on it the second day...  I did, however, specifically shop for a configuration that was known linux-friendly (i.e. Intel 3945 wireless and 7950GTX video).  The only issue remaining is that the hard disk access is not as fast as it should be, due to the system BIOS not having an AHCI option for SATA.  It's not a big problem, but I wish there was a BIOS fix for it.  Everything else works great, and I've even got the system LEDs to be software controlled under Linux with a beta release of libsmbios.

Anyway, my advice would be to try a newer release...

---

### Post by Arrdee on 2007-07-04
Try to do the partitioning with another live CD, like GParted.

---

