---
title: "Take off Windows? How to?"
date: 2009-01-25
forum: General Help
---

### Post by Budd Manlove on 2009-01-25
I finished installing Ubuntu and I think it's about time that I get this crap Windows off of here. The registry in Windows is pretty messed up... beyond repair. Almost half of the Windows functions do not work (my fault so I won't go blaming any imaginary little brother of mine). 

Is there a way I can remove Windows fully without killing my computer?

---

### Post by sports fan Matt on 2009-01-25
How did you set up your partitions? Did you tell it to use the entire space of the drive?

---

### Post by Crafty Kisses on 2009-01-25
You could technically download the GParted Live-CD, burn it, then boot it. You can grab the Live-CD right here [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). If you already have Ubuntu installed, which I'm assuming you do, you need to find the NTFS or FAT32 partitions, delete those partitions, then resize your ext3 partition to your liking. Now if you don't already have Ubuntu installed, you can always pop in the Ubuntu Live-CD and select "Guided Partition: Use entire disk" and that will just install Ubuntu over Windows, it's really your choice.

---

### Post by Budd Manlove on 2009-01-25
I already have Ubuntu installed and when I was trying to find info on how to do this before making this thread, I kept finding all this info about partitions. Now, I'm kind of a n00b when it comes to installing another entire OS. Where I'm going with that is... I have no idea what a partition is or where to find it. 

So with Ubuntu already installed, I just need to find the two partitions stated above and delete them? Where do I find them and how far should I expand the remaining one?

---

### Post by Budd Manlove on 2009-01-25
Bump* Any help with this anyone?

---

### Post by Crafty Kisses on 2009-01-25
Can you please post the results of this command?
```
sudo fdisk -lu
```
Once I or someone else has seen that command, we can help you further. If you do not know what a partition is, I recommend you reading this [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning). You need to find the NTFS or FAT32 partition, once you download the GParted Live-CD. Then you have the option to delete the NTFS/FAT32 partition and resize your ext3 partition to what you want. Another thing you can do is once your in the GParted Live-CD take a screenshot and again I or someone else can help you further.

---

### Post by Budd Manlove on 2009-01-25
Here are the results:
--------------------------------
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders, total 114270345 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   104310044    52106827+   7  HPFS/NTFS
/dev/sda4       104310045   114254279     4972117+  db  CP/M / CTOS / ...
--------------------------------

I will definitely read into that wiki that you've linked. Afterwards, I need to download the GParted Live-CD, burn it, then I will find the option to delete the two partitions and resize the ext3. 

I really appreciate the help. I will work on getting that done now.

---

### Post by Crafty Kisses on 2009-01-25
According to this:```
/dev/sda2 * 96390 104310044 52106827+ 7 HPFS/NTFS
```It's a NTFS partition, so in GParted look for the NTFS partition, once you have located the NTFS partition, give us a screenshot then we can further assist you.

---

### Post by Budd Manlove on 2009-01-25
I tried to take a screenshot but it went somewhere that I can't find. "/root" something. Either way, I just deleted the NTFS and it now has the following:

/dev/sda1 fat16 DellUtility Size=47.03MiB Used=7.86MiB Unused=37.17MiB
unallocated unallocated Size=46.69GiB Used=-- Unused=--
/dev/sda4 fat32 DellRestore Size=4.74GiB Used=4.49GiB Unused=261.11MiB
unallocated unallocated Size=7.84MiB Used=-- Unused=--

So restart.... "Invalid or damaged Bootable Partition"

Uh oh. Is there a step I missed?

---

### Post by Budd Manlove on 2009-01-27
Anyone have any help with resolving this?

---

### Post by oldos2er on 2009-01-27
Do you have two hard disks? There's no sign of Ubuntu on sda1.

 It appears the NTFS partition you deleted was a primary partition, and somehow gparted was unable to create a good partition table after you deleted it.

---

### Post by jocko on 2009-01-27
Well, it looks like you have deleted your windows partition, but I didn't see any linux partition in your fdisk output.
How did you install ubuntu? Did you use wubi to start the installation from within windows? In that case ubuntu was installed within your windows partition, which means it is gone now. You need to install ubuntu again.

The other partitions on your hard drive seem to be dell's utility partition and some dell restore partition. I guess the restore partition can be used to restore windows, so you may want to keep it in case you decide you need windows, unless you have a real windows install cd and a valid licence...
If you want to keep those partitions, just let ubuntu use the rest of the space on the hard drive without touching the other partitions.
If you don't want to keep them, make sure you remove them before you start to install ubuntu, and just let the ubuntu installer use the entire hard drive.

---

