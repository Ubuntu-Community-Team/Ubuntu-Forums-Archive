---
title: "[SOLVED] Problems installing on a SATA hard drive"
date: 2008-12-13
forum: General Help
---

### Post by chrisinspace on 2008-12-13
I am converting my old Vista gaming PC into a Mythbuntu box for my living room.  The hardware is a few years old, but I thought it would be well-suited for this purpose.  It is an AMD 64 on an Asus A8V-X motherboard with a WD Caviar 200GB Serial ATA HD (7200RPM/8MB/S-ATA-150).  I have tried for hours to get the installer to detect the disk, but with no luck.  

I am trying to install Mythbuntu 8.10 64bit, however I posted this as "all variants" because I don't think this problem is related to the MythTV packages.  I can see the drive in the BIOS, and if I boot from the hard-drive, my old Vista installation starts right up.  I tried turning ACPI off and back on, turning all of the hard drive features in the BIOS off (LBA/Large mode, Multisector Transfer, SMART Monitoring, 32-bit Data Transfer), and reseting the BIOS back to factory defaults.  I can boot the live disk and even see my hard drive activity light flashing as the system loads the live desktop, but when I run the installer, I don't see the hard drive when I get to the partitioning step.  It scans for disks but finds nothing and at that point, I am stuck.

I read through lots of posts last night and tried some suggestions, but couldn't get it to work.  I read several times about SATA drivers, but couldn't locate any for my hdd.  I checked the WD website, but all I saw were Windows drivers.  

Any help would be greatly appreciated.

---

### Post by chrisinspace on 2008-12-13
Well, I resumed my search today and I found [_this post_]("http://ubuntuforums.org/showthread.php?t=902561").  The suggestion in the first reply worked for me.  In the boot options, I hit F6 and added "all_generic_ide", without quotes.  

This allowed me to run the installer from the live desktop.  After a reboot, I have a functioning Mythbuntu machine!

---

