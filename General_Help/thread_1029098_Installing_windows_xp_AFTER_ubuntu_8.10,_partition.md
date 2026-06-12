---
title: "Installing windows xp AFTER ubuntu 8.10, partition detecting error"
date: 2009-01-03
forum: General Help
---

### Post by haru1ove on 2009-01-03
I have a problem installing xp...
This probably is a rare case

Running Toshiba Laptop
Running Hackintosh and Ubuntu
(installed hackintosh first and then ubuntu. Multi boot using ubuntu GRUB)
I created NTFS partition using GParted
using ONE hard drive

Currently, My partitions are like this-------

sda1= fat 32            200mb       (hackintosh EFI)
sda2= hfs+              96.22gb     (hackintosh)
Unallocated           128mb
sda3= linux-swap     477mb       (linux swap)
sda4= ext3              10.25gb     (ubuntu)
sda5= ntfs               4.53gb

When I boot from XP cd, 
It says my hard drive is empty, and shows F: ONLY

Its like

F:            120gb free out of 120gb

Will you guys be able to help me at all?
the NTFS partition works fine on ubuntu and hackintosh....

Thanks in advance!

---

### Post by mikeman141 on 2009-01-03
XP installation disks don't often recognize newer hardware...for example, SATA drives.  I had a similar problem, maybe this will help


[http://news.softpedia.com/news/Install-Windows-XP-POn-SATA-Without-a-Floppy-F6-47807.shtml]("http://news.softpedia.com/news/Install-Windows-XP-POn-SATA-Without-a-Floppy-F6-47807.shtml")


it did for me.


you probably need to slipstream other drivers into the XP install disk.

---

### Post by jrusso2 on 2009-01-03
I have seen this issue with gparted in making NTFS partitions.  There seems to be some way they don't understand the partition boundries.  I would make the NTFS partition using a something else.

---

