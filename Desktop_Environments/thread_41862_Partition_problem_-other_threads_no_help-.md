---
title: "Partition problem -other threads no help-"
date: 2005-06-15
forum: Desktop Environments
---

### Post by odbod on 2005-06-15
I am new to Linux. I don't know if  am in the right thread. I have been messing with Knoppix for a while and have decided to use Ubuntu as a seperate OS to my Windows 2000. 

I only have a 10.1 gb hard drive with 4 gb of free space. I want to take aways only 2 gb of it for Ubuntu. The thing is, I don't get what the guide is telling me on partitioning.

What would really be appreciated is info on what partitions Ubuntu Linux can run on. I have partition magic to help me out with this.

Is it Ext2/3? Can it be on FAT32? I need help. I do not want to lose my data for windows.

Also.. When I do this and get Ubuntu installed, will I be able to access my NTFS partition?

---

### Post by defkewl on 2005-06-15
Ext2/3 is good enough. But nowadays people tend to recommend reiserfs.

If you want to access your NTFS partition you need to install some plugin or compile your kernel so it can support NTFS partition

---

### Post by Alexander Kirillov on 2005-06-15
[QUOTE=odbod]I am new to Linux. I don't know if  am in the right thread. I have been messing with Knoppix for a while and have decided to use Ubuntu as a seperate OS to my Windows 2000. 

I only have a 10.1 gb hard drive with 4 gb of free space. I want to take aways only 2 gb of it for Ubuntu. The thing is, I don't get what the guide is telling me on partitioning.

What would really be appreciated is info on what partitions Ubuntu Linux can run on. I have partition magic to help me out with this.

Is it Ext2/3? Can it be on FAT32? I need help. I do not want to lose my data for windows.

Also.. When I do this and get Ubuntu installed, will I be able to access my NTFS partition?[/QUOTE]
 Ubuntu uses ext3 by default - and for new users, it is suggested that you do use the default. However, Ubuntu installer can create the filesystem itself - it just needs some free (unpartitioned) space to do it (which you can create by resizing the existing partitions with Partition Magic). 

However, 2Gb  is not much. I guess it will be possible to install, but you will have to be very careful and install only the bare minimum of apps. 

Ubuntu can read NTFS partition, but not write to it. 

For more info, check this:
 [https://wiki.ubuntu.com//LinuxFilesystemsExplained/](https://wiki.ubuntu.com//LinuxFilesystemsExplained/)

---

### Post by Seti on 2005-06-15
If you already have the free space (4 GB?) then don't bother with partition magic AT ALL, that program is a PITA IMHO. Just use the partitioning tool on the Ubuntu installer disc to set up the 4 Gb of free space for Ubuntu. Depending on how much RAM you have, you may want to set up a /swap partition. Like, if you have 256 MGb of RAM, make a half-gig swap space. The installer sets all this up. You can then make the remaining 3.5 gigs a reiserfs partition for linux. The installer will see your windows partition and add it to GRUB, the  bootloader.
And you should have no problems reading data from your NTFS partition from Ubuntu, but use the 4 gigs of free space for linux; you'll thank yourself later.

---

### Post by odbod on 2005-06-15
DId you  stop to think about the rest of my windows 2000 space?


Would 2,568 mb work? I am trying to figure how much over 2gb I should use.

---

### Post by odbod on 2005-06-15
Ok... my mom's boyfriend did something to the partitions to make it work then I had a problem getting zlib on. I tried getting into windows 2000 and it said "No poerating system found". The NTFS partition still exists and its primary. Should I just put Linux on it by just formatting the entire drive and putting it on?

---

### Post by ltmon on 2005-06-15
[QUOTE=odbod]Ok... my mom's boyfriend did something to the partitions to make it work then I had a problem getting zlib on. I tried getting into windows 2000 and it said "No poerating system found". The NTFS partition still exists and its primary. Should I just put Linux on it by just formatting the entire drive and putting it on?[/QUOTE]

OK That sounds nasty  :? Your mom's boyfriend possibly blasted your partition table.  I personally don't know how to rescue you from this one.

If you do decide to start from scratch I would do it in the following order:

1. Partition your hard disk into 2 partitions, one for Windows, one for Linux.  You could boot up into knoppix to do this (I think it comes with a tool called qtparted).  Don't bother setting up filesystems here.  I feel that 2GB would be a bit thin for Ubuntu, 4 would be much much better.

2. Install Windows on the FIRST partition... it can go ugly if you install it after Linux (Windows doesn't play well with others :( )

3. Install linux on the second partition.  During the linux install you should split this into a swap partition and an ext3 (default) partition.  This should really be mainly automatic in Ubuntu.

4. Have fun.

Hope it all sorts itself out.

L.

EDIT: It doesn't sound like you have this luxury... but if you have extra space, format it as FAT32 and use it for shared storage.  Both windows and linux can read and write to FAT32, but I would not use this as a primary partition for either operating system.

---

