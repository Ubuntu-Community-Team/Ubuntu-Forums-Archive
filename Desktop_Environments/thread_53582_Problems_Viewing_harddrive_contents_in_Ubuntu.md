---
title: "Problems Viewing harddrive contents in Ubuntu"
date: 2005-08-01
forum: Desktop Environments
---

### Post by bruin03 on 2005-08-01
I was pleased w/ my first installation last week, I tried installing Ubuntu on a second box.

fdisk -l results:
```
Disk /dev/hda: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1788    14362078+  83  Linux
/dev/hda2            1789        1868      642600    5  Extended
/dev/hda5            1789        1868      642568+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14596   117242338+   c  W95 FAT32 (LBA) 

Disk /dev/sda: 128 MB, 128974848 bytes
8 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         979      125296    6  FAT16

```

etc/fstab looks like
```
/dev/hdb1 /media/windows vfat    iocharset=utf8,umask=000   0       0 
```

I am trying to mount Hdb1, which shows in fdisk as 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14596   117242338+   c  W95 FAT32 (LBA) 
```
but when I browse to the media/windows/ it shows 0 files and only 111Gigs of space available.
QUESTIONS:
1. How come I can't see my files?
2.  What do I need to do to view my files?

---

### Post by bruin03 on 2005-08-01
Any insight? Is this a permissions problem?  :-?

---

### Post by Hairy_Palms on 2005-08-01
see if you can mount it somewhere else, eg make a folder in home called win and type 

sudo mount -t vfat /dev/hdb1 /home/bruin03/win 
then see if you can read it.

---

### Post by bruin03 on 2005-08-01
[QUOTE=Hairy_Palms]see if you can mount it somewhere else, eg make a folder in home called win and type 

sudo mount -t vfat /dev/hdb1 /home/bruin03/win 
then see if you can read it.[/QUOTE]

root@ubuntu:/home/bruin03/win # -t vfat /dev/hdb1 /home/bruin03/win

I tried to mount using the above command and got the following error:
[B]
bash: -t: command not found[/B]

***Edit***
I am using Hoary 5.04 by the way.

---

### Post by bruin03 on 2005-08-01
[QUOTE=bruin03]root@ubuntu:/home/bruin03/win # -t vfat /dev/hdb1 /home/bruin03/win

I tried to mount using the above command and got the following error:
[B]
bash: -t: command not found[/B]

***Edit***
I am using Hoary 5.04 by the way.[/QUOTE]

**UPDATE**
I made a typo in the terminal anf forgot to put "mount"
I was able to mount the drive to /home/bruin03/win but it's still showing 0 files and listing the free space of the drive as the drive size.  :-? 

I'm wondering if my problem is similar to the one described here: [http://www.linuxquestions.org/questions/showthread.php?threadid=87656](http://www.linuxquestions.org/questions/showthread.php?threadid=87656)

How would I fix this in Ubuntu?

---

### Post by brousch on 2005-08-01
I am surprised that you were able to make a 111Gig FAT32 partition. The other day I tried to make a 73Gig FAT32 partition and Windows XP would not let me. I had to chop it up into 3 partitions.

Is it possible that you formatted your partition through linux, and it didn't check for a valid maximum size?

Please don't go changing anything because of this post, I am just trying to offer up suggestions for discussions.

---

### Post by bruin03 on 2005-08-01
[QUOTE=brousch]I am surprised that you were able to make a 111Gig FAT32 partition. The other day I tried to make a 73Gig FAT32 partition and Windows XP would not let me. I had to chop it up into 3 partitions.

Is it possible that you formatted your partition through linux, and it didn't check for a valid maximum size?

Please don't go changing anything because of this post, I am just trying to offer up suggestions for discussions.[/QUOTE]

Well, I never partitioned the drive, that is probably why. I had purchaed the drive used, formatted it in dos, and and used it as a spare filestorage drive in windows.
I'm trying to understand why I can't see it's contents in linux  :-|

---

