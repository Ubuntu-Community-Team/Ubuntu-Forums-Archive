---
title: "Sys reguirements for ubuntu ultimate"
date: 2009-01-22
forum: General Help
---

### Post by niwatori1 on 2009-01-22
ok i have a couple guestions.
im going to dual boot between windows and linux with 2 separete
HDD's one linux one windows.
In the mean time i have a secondary 500 gig HDD to aid the two 40 Gigs that house my os's. 
is there a file format that allows me to use the 500 gig on both os's or will they both see it as jump drive(ideal)?
second. When i was formating my second HDD for windows i accedentaly formated my linux install. so im starting from scratch.
my plan is to install ubuntu ultimate edition. But i dont know if my computers good enough to run fusion on it along with all the other bells and whithels 
I have the following
CPU;Pentium 4 2.4 ghz
RAM;1 gig generic
GRAPHICS;Nvidia Geforce 6600 
HDD;Standard 40 gig
CD-ROM;Sony DVD-RW combo drive
SOUND;Generic PCI Sound card

Any help would be appreceated
Thanks:D

---

### Post by mssever on 2009-01-23
> **niwatori1 said:**
> is there a file format that allows me to use the 500 gig on both os's or will they both see it as jump drive(ideal)?
If you format it as NTFS, both Windows and Linux will be able to use it, but Linux permissions won't apply. If you format it as ext3, you'll be able to access it from Windows if you install the Windows ext2 driver. However, Linux permissions won't apply from Windows, and because the Windows driver is ext2, not ext3, you'll lose journalling from the Windows side.
> second. When i was formating my second HDD for windows i accedentaly formated my linux install. so im starting from scratch.
my plan is to install ubuntu ultimate edition. But i dont know if my computers good enough to run fusion on it along with all the other bells and whithels 
Try it out from the live CD. If the live CD starts with Compiz running, than it works with your video card. Otherwise, it probably doesn't. This is for the standard Ubuntu live CD. I'm not familiar with Ubuntu Ultimate, so it might or moght apply. You could also google your video card model and compiz to see what you learn.

---

