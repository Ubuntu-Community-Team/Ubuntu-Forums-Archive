---
title: "lucid freezes when starting administrative applications"
date: 2010-08-24
forum: Desktop Environments
---

### Post by two4two on 2010-08-24
I use 64-bit desktop of Kubuntu, Ubuntu studio, xubuntu, and Ubuntu veriosn 10.4 LTS.  They all have their problems.  I could not get ANY of them to install using the CD because I got errno5: input/output error for various files.  I verified the disks in all ways but still they would not work.  I finally used universal USB installer which did in fact finish the install for Xubuntu.  But the problem came up that I experienced many time on Ubuntu Studio 9.10 64-bit:  whenever I try to do anything that requires my password (starting administrative applications) it freezes dead.  At this time the hard drive is in continual access.  The only way is to hit reset and reboot.  Sometimes in Ubuntu Studio it freezes at other times, but the administrative thing is a sure-fire way to freeze.  How do I determine what is causing the problem?  When I use the live CD it works just fine.  I can browse the logs on the installed file system(s).  What should I look for to see what was executing at the time it froze?  As far as my situation goes I simply can't use Ubuntu of any version until I get this resolved.

I have an older home-built PC:

AMD 64 X2 4400
Asus A8V with 3 GB memory
one Maxtor IDE 250GB HD, one WD IDE 500GB HD
one IDE Lite-on DVD-RW
One SATA LG GGW-H20L Blu-ray RW connected to the VIA controller (the same for the IDE devices -- all conected to the VIA controller)
The Promise controller is enabled in the BIOS in IDE mode, but nothing is conected to it, the LAN and firewire are diabled in the BIOS
There is a multi-device conected to one of the USB headers that has USB, SD, mini-SD, etc.
I have a D-Link DWA-160 (dual band -150/300) conected to a USB, but there is no Linux driver for it so it is not recognized in Ubuntu, so I also have a D-link DWL-122 10MB conected to another USB and this is what Ubuntu has a drtiver for and recognizes and uses.
I have ATI Radeon 4650 AGP 8X with the free driver (not the proprietary driver), but if I do enable the proprietary driver it does not solve the freeze problem
I have an ENLTV vid/cap which Ubuntu recognizes and will use
And I have a Real Magic XCard which Ubuntu has no driver for (yet!).

This is all I can think to include.  I hope someone can help me to identify what causes these freeze-ups.

---

### Post by two4two on 2012-05-08
It was a bad motherboard.

---

