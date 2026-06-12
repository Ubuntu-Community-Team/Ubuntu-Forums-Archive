---
title: "MDADM problem: partition lost because of mkfs.ext3"
date: 2008-11-04
forum: Desktop Environments
---

### Post by trivet on 2008-11-04
hi

i have a RAID 1 system with 2 drives: /dev/sdb1 and /dev/sdc1. I use MDADM to create the raid 1 named /dev/md0. I have lot of data there. The problem is that i was re-installing system and from the live cd i executed a:
mkfs.ext3 /dev/sdb1
mkfs.ext3 /dev/sdc1

then installed Ubuntu again wihtout formating those drives because my system is installed in /dev/sda

the problem is that when i try to re-create the raid and mount it, it does not contain any file. i did this more time before and always worked BUT never used the mkfs.ext3 (that was a mistake). anyhow knows how to recover data or fix the problem?

thanks in advance
trivet

---

### Post by psusi on 2008-11-05
Hope you have a backup.  Once you format the partition the data is gone.

---

