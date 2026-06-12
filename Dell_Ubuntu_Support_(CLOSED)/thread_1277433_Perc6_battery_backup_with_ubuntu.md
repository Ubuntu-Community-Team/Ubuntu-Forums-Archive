---
title: "Perc6 battery backup with ubuntu"
date: 2009-09-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ha2432003 on 2009-09-28
I have a Dell Poweredge 1950 with a Perc6 RAID controller running ubuntu 8.04.  Using Dell's omreport tool, I am able to verify that the battery is functioning properly.  I've set the write policy to 'Write Back'.

Over the past two years I've suffered two power outages.  In both instances the disk didn't pass fsck on reboot.  I'm running MySQL on the machine and, in both instances, the innodb database became corrupt.  Given that innodb is ACID compliant, I can only assume that this is a hardware issue with the RAID controller.

Does anyone have any experience with the perc6 controller and battery backup?  Is it not to be trusted?  Should I stick with a write through policy?

---

### Post by wgarider on 2009-10-01
I have about 50 1950's with the PERC 6 - I've not had any issues with the batteries. While I run Windows on them for the most part, my suggestion would be to stick with the write through.

---

