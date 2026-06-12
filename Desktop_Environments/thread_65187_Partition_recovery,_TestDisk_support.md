---
title: "Partition recovery, TestDisk support?"
date: 2005-09-13
forum: Desktop Environments
---

### Post by juhis on 2005-09-13
Hello,

Can anyone tell me how to use TestDisk? PartitionMagic lost my Ubuntu-/root-directroy after some resizing and moving. TestDisk is able to find old markings for /root-directory, PLUS new and old markings for other directories which should be ok. So I can figure out the exact cylinders where the to-be-new-root-directory could start and end (= where partition magic has moved it, if I have understood right). Maybe I can somehow recover it then...? 

Fdisk or fsck couldn't understand the partition, should I give a shot to sfdisk or cfidsk or parted on install-cd before hassling with TestDisk? Or is it easiest just to reinstall Ubuntu?

I'm afraid to do anything concrete with TestDisk since Partitionmagic gave me such a rough ride.

---

### Post by KingBahamut on 2005-09-13
From a data recovery standpoint, Id say yes, give a partitioner like cfdsik or parted one first. Just to see if  your paritition is seen. If its not, then you may have corrupted the maint. partition on your drive ( one of those things you never see ). 

How critical is the nature of data on the drive?

---

### Post by juhis on 2005-09-13
[QUOTE=KingBahamut]From a data recovery standpoint, Id say yes, give a partitioner like cfdsik or parted one first. Just to see if  your paritition is seen. If its not, then you may have corrupted the maint. partition on your drive ( one of those things you never see ). 

How critical is the nature of data on the drive?[/QUOTE]

Data is not very critical, I would just have to reinstall ubuntu and all packages and to make them work = lot of work. PartitionMagic is able to see the root-partition, but it tells it's full (5 GB, before operation it took something like 2,5 GB of 7 GB) and thinks it's a ext2 although it's ext3. I'm curious about saving it cause I'm suspecting all the information is there.

---

