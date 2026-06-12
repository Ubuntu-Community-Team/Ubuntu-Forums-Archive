---
title: "FAT32 missing data problems between WinXP &amp; Ubuntu"
date: 2006-04-22
forum: Desktop Environments
---

### Post by onyxrev on 2006-04-22
Heyo...

Having some really annoying problems with a FAT32 partition on my laptop's hard drive.  I use Ubuntu primarily for everyday computing tasks and dual boot into Windows XP Home for some music production, backup, and Flash work  

When I save files to the FAT32 partition from Ubuntu and then do substantial access the drive from Windows the files I wrote to the drive in Ubuntu disappear.  

Say, for instance, I do a research paper and save it to the FAT32 partition in Ubuntu.  I use Acronis TrueImage in Windows XP to do backups of my Ubuntu Ext3 partition and I generally save this data (about 2GB compressed) to the very same FAT32 partition that stores my research paper.

Upon booting back into either Windows or Ubuntu the research paper will more often than not simply be gone.  And running ChkDsk /R or /F will not recover it, although errors are generally found (but not bad sectors).

Short of an hard drive problem what could be the cause of this?  I thought FAT32 was really solid between the two OSes.

Here's my fstab...

proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda1 /media/windows ntfs umask=0222,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda4 /media/shared vfat umask=0000,uid=0,gid=0,auto,rw,nouser 0 0


I really hope you folks can help because not trusting my partitions is freaking me out!  Thanks!

---

### Post by Sutekh on 2006-04-23
There is nothing wrong with your fstab.  

The only thing I can think of is what was used to format the partition.

I had this problem ages ago, I'm sorry to say I don't remember what fixed it.  I could write to the partition in Ubuntu, but these writes did not show up in Windows.  Somewhere along the line it just started working properly.  This partition was formatted using the Ubuntu installer.  It's been re-formatted since.

For some reason, now when I use GParted to format a FAT32 partition, it is seen by Ubuntu as ext3, and by Windows as unrecognised.  I had to use the [Ext2 Installable File System For Windows](http://www.fs-driver.org/) to access the partition in Windows.  Despite this I have been able to write files between OS.

---

### Post by onyxrev on 2006-04-23
Sutekh... that Ext2 driver looks like a great solution.  I have never liked FAT.  Is it stable and reliable??

---

### Post by onyxrev on 2006-04-23
I was reading the FAQ on the FS-Driver.og site and I realized that I've been using the WinXP hibernate feature to move between the OSes.  I bet that has something to do with the problems I've been having in that disk writes that have been delayed were not permanently saved... anyone agree?

---

