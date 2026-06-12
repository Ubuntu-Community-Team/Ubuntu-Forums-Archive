---
title: "Two hard drives?"
date: 2010-09-05
forum: Desktop Environments
---

### Post by stair314 on 2010-09-05
How can I get Ubuntu to recognize that I have two internal hard drives? I installed Ubuntu on a brand new machine with no OS on it, and now if I look at "/" in the File Browser, the window says "24 items, Free space: 403.3 GB" at the bottom. Since each of my hard drives has 500 GB on it and I haven't installed a ton of stuff yet, it looks like just one is being used. Also, from the "Computer" window, only "File System" ("/") and the optical drive are visible.

---

### Post by 3Miro on 2010-09-05
Go to Applications -> Accessories -> Terminal and type in it:
```
sudo fdisk -l
```
this will list all hard-drives and all partitions. You can post the result here to see what is happening.

Another command is "df" (disk free) that will tell you how much space you have on each partition.

You can also install Gparted, which is a graphical program that will allow you to create/delete partitions as well as "mount" them.  Mounting a partition will associate a partition of your hard-drive with a folder on your computer(usually /media/something). Then any file you put into the folder, effectively get written into the partition.

You can also read on /etc/fastab for more advanced management of partitions (if you are interested in the inner workings of Ubuntu on a more professional level).

---

### Post by Nythain on 2010-09-05
you can type
```

sudo fdisk -l

```
in a terminal to make sure that ubuntu knows you have the second drive.

after that, does the second drive have a filesystem on it? if so, what filesystem e.g. ext3, ext4, ntfs, fat, etc

more than likely, either the hard drive isnt formatted yet, even if it had ntfs "places" and the file browser nautilus would usually see it and give the option of mounting it for browsing.

---

### Post by stair314 on 2010-09-05
Here's the output of df:
> 
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            461229088  14935224 422864796   4% /
none                   6155892       360   6155532   1% /dev
none                   6160404       276   6160128   1% /dev/shm
none                   6160404       192   6160212   1% /var/run
none                   6160404         0   6160404   0% /var/lock
none                   6160404         0   6160404   0% /lib/init/rw
/dev/sr0               4453556   4453556         0 100% /media/DVDVolume


Here's the output of sudo fdisk -l:
> 
$ sudo fdisk -l
[sudo] password for <username>: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051ee7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58336   468581376   83  Linux
/dev/sda2           58336       60802    19803137    5  Extended
/dev/sda5           58336       60802    19803136   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System


I assume this means it's detected but not partitioned, so I should partition it in gparted?

---

### Post by stair314 on 2010-09-05
OK, thanks! Got it set up in gparted, then configured /etc/fstab using this article:

[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)

---

### Post by 3Miro on 2010-09-05
You seem to have one partition that is associated with / one associated with "swap", both of which on the first hard drive. You cut the output on the second hard-drive right before it lists the partitions. Is this all that you get from "fdisk -l", if so, then you need to partition the second hard drive using gparted.

This is getting late for me, if you have anything more on "fdisk -l" please post it. Otherwise, I will try to look at this in the morning.

EDIT: Glad you resolved it.

---

### Post by stair314 on 2010-09-05
Thanks for the help. Yeah, I resolved it / the output wasn't cut off, it was just non-existent because there were no partitions there yet.

---

