---
title: "Formatted wrong harddrive"
date: 2008-11-04
forum: Desktop Environments
---

### Post by schurtek on 2008-11-04
OMG!!! I can't believe I did this?

Long story short: I have two 250GB Hard Drives. One has all my company data on it... the other has Ubuntu on it... I backed up the Ubuntu one to my external 500GB HDD. Then I switched off the machine, unplugged the drive, and then installed Intrepid. One problem... I unplugged the wrong drive... I know have two 250GB Hard Drives with different versions of Ubuntu on? What do I do!

---

### Post by taurus on 2008-11-04
_Stop_ using the harddrive that contained your company's data.  Take it to a professional and see if they can do anything to recovery the data on it.

---

### Post by schurtek on 2008-11-04
okay... here is my problem... I am the only local person who supports anything based on linux... I can promise you, they will tell me they can't help me as it was EXT3.

I have tried TestDisk, but it only picks up the current partitions. I want to recover the partition from before... less than 5% of the disk is written...

---

### Post by gusst250 on 2008-11-10
I tried testdisk today. I was about to install 8.10 and chose the alternative guided partition - use entire disk. Very foolish, but I thought I would get some kind of a warning when the entire was about to be formatted. I remember numbers of warnings about that from 8.04 installation.

After a cold sweaty hour of many cups of coffee and lot of nervous guitar playing testdisk finally told me it had recovered some of my partitions from before. Luckyli the one I hoped for, the one with all data on it. (not the operatives). It went quite smooth, after testdisk had found the old partitions i was able to write a new partition table to the hd which allowed me to reboot and then copy my files to (a temporary borrowed) external hd before I reinstalled all OS.

//Gustav

---

### Post by schurtek on 2008-11-12
> **gusst250 said:**
> I tried testdisk today. I was about to install 8.10 and chose the alternative guided partition - use entire disk. Very foolish, but I thought I would get some kind of a warning when the entire was about to be formatted. I remember numbers of warnings about that from 8.04 installation.

After a cold sweaty hour of many cups of coffee and lot of nervous guitar playing testdisk finally told me it had recovered some of my partitions from before. Luckyli the one I hoped for, the one with all data on it. (not the operatives). It went quite smooth, after testdisk had found the old partitions i was able to write a new partition table to the hd which allowed me to reboot and then copy my files to (a temporary borrowed) external hd before I reinstalled all OS.

//Gustav

It seams we are in the same boat... except I wiped out one EXT3 data partition. Please can you put a step by step and play by play of exactly what you did... so that I can achieve the same... I will get my Guitar out, and drink lots of Coke (coffee doesn't agree with me...) - oh, what songs where you playing... maybe I need to play the exact music as you... :guitar:

---

