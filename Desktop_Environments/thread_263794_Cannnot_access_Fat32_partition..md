---
title: "Cannnot access Fat32 partition."
date: 2006-09-23
forum: Desktop Environments
---

### Post by katalyst23 on 2006-09-23
Hi guys, I just switched to Ubuntu a couple of days ago.  So far I have only this one complaint - I can't access my Fat32 partition.

I have 2 hard drives - an 80 gb Pata, with Linux on it ( I previously had Suse on there), and a 160 gb SATA, with Windows XP and a FAT32 partition.I formatted the partition with GParted, and I could access this FAT32 partition fine from Suse, but can't seem to get it to work now.  

Here is the line from my fstab:

/dev/sda2     /media/satadata   vfat   auto,user,exec,rw,umask=0000   0   0


Yes, I have the directory /media/satadata created. =)

fdisk -l gives me this concerning my SATA drive : 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1       10313    82839141    7  HPFS/NTFS
/dev/sda2           10314       19456    73441147+   b  W95 FAT32




But fdisk /dev/sda2 says that 

Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 258206.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)


When I ask fdisk to print the partition table for it it reads:

Disk /dev/sda2: 2123.8 GB, 2123819520000 bytes
255 heads, 63 sectors/track, 258206 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System

When I grep for the drive in dmesg this is what it reads:

[   30.289421]  sda: AHDI sda1 sda2
[   48.418674] VFS: Can't find a valid FAT filesystem on dev sda2.
[   62.342138] Buffer I/O error on device sda2, logical block 518510608
[   62.342493] Buffer I/O error on device sda2, logical block 518510608
[   62.342645] Buffer I/O error on device sda2, logical block 518510624


I booted into Windows and ran chkdisk and defragged the partition to see if that would help.  It didn't, so I'm a bit stumped as to what to try next.  I'm a little leery of dosfscking the partition because I can access it just fine from Windows, and I'm scared it will mess up the data on it.  Do you guys have any suggestions as to what to try?

Edit:  Whoops, I also forgot to mention, I don't know if it's relevant, but, I tried launching the disk manager to see if I could view disks from there, and it just hangs.

---

### Post by katalyst23 on 2006-10-14
Okay, no one answer my thread, but I thought I would post how I fixed things in case someone else searches the forums and finds this and has the same problem.  

I tried using TestDisk to scan the SATA drive, but no beans, it didn't even detect any of the partitions! It did give me an error message about the partition table being off, but then couldn't find any partitions.  I tried fiddling with TestDisk for a while... carefully.. then got aggravated.  

So I booted into Windows, moved everything off the FAT32 partition onto the NTFS partition, then ran a GParted LiveCD.  I reformatted the FAT32 partition first, thinking I would probably also have to delete and remake it, but decided to boot into Ubuntu to check anyway.

Lo and behold! When I boot up, there is the partition's icon on my desk, it mounted fine and everything, and I can access/delete/whatever to my files now.  

If anyone comes across this, and knows why Linux had issues with this partition and Windows do it, I would love an explanation.  Even GParted couldn't read the file system until I reformatted.

---

