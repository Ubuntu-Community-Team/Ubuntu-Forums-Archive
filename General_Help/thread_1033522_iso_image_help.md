---
title: "iso image help"
date: 2009-01-07
forum: General Help
---

### Post by sPiN1 on 2009-01-07
I want to dual boot windows and ubuntu so I can still play games easily on windows and have the enjoyment of linux but I need to burn this ISO to a disc, which I can do but the problem I've run into is the file is a few MB too big... What I need help with is how to get into the ISO and delete something like windows touring or something like that so I can burn it. Any help would be much much appreciated! Thanks in advance!

---

### Post by oilchangeguy on 2009-01-07
> **sPiN1 said:**
> I want to dual boot windows and ubuntu so I can still play games easily on windows and have the enjoyment of linux but I need to burn this ISO to a disc, which I can do but the problem I've run into is the file is a few MB too big... What I need help with is how to get into the ISO and delete something like windows touring or something like that so I can burn it. Any help would be much much appreciated! Thanks in advance!

where are you getting this iso from? if it's from [www.ubuntu.com](www.ubuntu.com) you'll have no problems.

---

### Post by Titan8990 on 2009-01-07
You can use something like DaemonTools to mount images in windows. I am not sure how much they can be altered however.

The ISO should be under 700Mb, the standard size of a CD.

---

### Post by oilchangeguy on 2009-01-07
also read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
and this:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by sPiN1 on 2009-01-07
Okay I'm currently ON Ubuntu and the ISO is Windows XP.

edit: and I know how to dualboot and everything just fine, I've done it plenty of times.

---

### Post by Titan8990 on 2009-01-07
report the output of:


sudo fdisk -l

---

### Post by donkyhotay on 2009-01-07
What do you mean 'it's too big', it's an ISO and should fit on a CD perfectly. What burning software are you using and (more importantly) are you burning the ISO onto your CD or are you burning the ISO data file onto your CD. There is a significant difference between the two and burning the data file onto the CD will not allow you to install. The following link may help as well.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by 2hot6ft2 on 2009-01-07
Gmount-iso is an easy way to mount iso images in a directory. it will always ask for admin password in order to mount though. It's in the repositories

---

### Post by sPiN1 on 2009-01-07
jason@jason:~$ sudo fdisk -l
[sudo] password for jason: 

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16363   131435766   83  Linux
/dev/sda2           29538       30017     3855600   83  Linux
/dev/sda3           30018       30394     3028252+   f  W95 Ext'd (LBA)
/dev/sda4           16364       29537   105820155   83  Linux
/dev/sda5           30018       30394     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order
jason@jason:~$
> **donkyhotay said:**
> What do you mean 'it's too big', it's an ISO and should fit on a CD perfectly. What burning software are you using and (more importantly) are you burning the ISO onto your CD or are you burning the ISO data file onto your CD. There is a significant difference between the two and burning the data file onto the CD will not allow you to install. The following link may help as well.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
The file was a .daa and I converted it to .iso with PowerISO

---

### Post by barbolanero on 2009-01-07
How big is the iso exactly? Just a couple extra MB's won't resent any problem. Somethingl like 702 mb should still burn on a 700 MB Cd. And for burning on Ubuntu I recommend Brasero Disc Burning. Just download it from Synaptic.

---

### Post by sPiN1 on 2009-01-07
> **barbolanero said:**
> How big is the iso exactly? Just a couple extra MB's won't resent any problem. Somethingl like 702 mb should still burn on a 700 MB Cd. And for burning on Ubuntu I recommend Brasero Disc Burning. Just download it from Synaptic.

It's 705.7 and my disc is a 700mb cd-rw and yeah I planned on using Brasero

---

### Post by Rocket2DMn on 2009-01-07
Closed for pirated software.

---

