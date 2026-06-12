---
title: "HardDrive problem"
date: 2009-01-03
forum: General Help
---

### Post by Inferno31 on 2009-01-03
Hey,
I cloned my old hdd to a new one. It kept both my partitions (Xp and Ubuntu), but it gave all the space to the windows partition. So I used livecd, and opened gparted to repartition this space to split it between the two partitions. 

It first gave me an error, but after a second attempt it gave me an error, but all my unallocated space dissiappeared! It had been added to my linux drive (ext3), but the amount of free space remained the same! :confused:  So I booted into ubuntu, and right clicked and checked and the size doubled (I can't find any new files) and the amount of free space is only still 1 gb (when it should be like 70+). Any help I'm completely lost and I don't know how to proceed. 

All my data is backed up as well for both drives (original HDD that I cloned).


I'm using ubuntu 8.10 and used a 8.10 live cd as well.

---

### Post by Inferno31 on 2009-01-03
Does anyone know where I could go for help?

---

### Post by kgriff on 2009-01-03
When you used gparted, did you first delete the existing partitions?  If not, try doing so, then recreate the partitions you want.  If that doesn't work, you may try using the Set Disklabel function, then recreate partitions.

You may have to use Windows fdisk to initially create a FAT partition, if that's what you're using for Windows.  I've had problems with Windows recognizing partitions created with gparted.  If you do have to use fdisk, just leave the portion that you want to use for Linux as unpartitioned space, then use gparted to partition it.

---

### Post by Inferno31 on 2009-01-03
> **kgriff said:**
> When you used gparted, did you first delete the existing partitions?  If not, try doing so, then recreate the partitions you want.  If that doesn't work, you may try using the Set Disklabel function, then recreate partitions.

You may have to use Windows fdisk to initially create a FAT partition, if that's what you're using for Windows.  I've had problems with Windows recognizing partitions created with gparted.  If you do have to use fdisk, just leave the portion that you want to use for Linux as unpartitioned space, then use gparted to partition it.

Hey thanks for response.

Is it required to delete the existing partitions (isn't this just a format then?) Because I want to maintain my data on both partitions, and I'm using NTFS for XP and there is no problem between either OS reading the other drive. The issue is when I tried to increase the size of my ext3 drive using the unalloacted space my drive capacity increased, but the amount of free space I had remained the same..

---

### Post by kgriff on 2009-01-06
I've never ran into the problem you're having, but I've seldom tried to resize a partition.
My normal approach, if I have a drive with multiple partitions and additional free space that I want to use is to create another partition using the free space.  I've known of too many people that have had issues resizing for me to believe it is a completely reliable process.

My suggestion, in your case, was simply to allow you get the partition sizes you wanted.  Yes, you would lose all of the data on those partitions, but, since you have the data elsewhere, you should be able to restore it.

You could also try a commercial utility like Partition Magic.

---

