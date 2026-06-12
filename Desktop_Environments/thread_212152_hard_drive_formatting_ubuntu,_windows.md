---
title: "hard drive formatting ubuntu, windows"
date: 2006-07-09
forum: Desktop Environments
---

### Post by paisa on 2006-07-09
Hi,
I just installed ubuntu on my pc, I have a partition containing Windows Xp, and another one with ubuntu. I still have 10 Gb free on my hard drive that I would like to use as a share partition FAT32. How can I create and format this partition without destroying any information on my hd.
Thanks for your help.

---

### Post by Choad on 2006-07-09
system > administration > disks

choose the correct physical drive

add a partition.... etc. 

it'll warn you in a big obvious warning message if you are about to format an already existing partition... so dont worry too much about accidentally ruining your computer.

its always advisable to back up the really important documents before messing with partitions tho!

---

### Post by paisa on 2006-07-10
Thanks for your advice.
I need to know what kind of software is safe to do so.

---

### Post by Sonofmoog on 2006-07-10
> **paisa said:**
> Thanks for your advice.
I need to know what kind of software is safe to do so.

GParted or qtparted in Linux; Partition Magic or BootItNG in Windows.  Please be aware that partitioning is always high risk business.  It's like flying - most times getting from here to there is not a problem, but when things go wrong, they *really *go wrong ..

---

### Post by DavidFL on 2006-07-11
> **paisa said:**
> Hi,
I just installed ubuntu on my pc, I have a partition containing Windows Xp, and another one with ubuntu. I still have 10 Gb free on my hard drive that I would like to use as a share partition FAT32. How can I create and format this partition without destroying any information on my hd.
Thanks for your help.

I used GParted to do exactly what you are wanting to do and it worked like a charm.  After formating I then had create the moun point with 'mkdir' then I had to edit my /etc/fstab file accordingly in order to be able to access it from Ubuntu.  Make sure to select the corrent unpartitioned space instead of an existing partition.

---

