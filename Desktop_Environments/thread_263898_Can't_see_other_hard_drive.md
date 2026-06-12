---
title: "Can't see other hard drive"
date: 2006-09-23
forum: Desktop Environments
---

### Post by superheavy on 2006-09-23
I installed Ubuntu Dapper Drake on my computer a week ago.  I have two hard drives, with Ubuntu on my master and my old XP on the slave.  However, when running my Ubuntu system I see no evidence of my XP/slave drive.  It does not show up under Device Manager, Disk, Gnome Partition Editor or in /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

But when I run Ubuntu from the LiveCd I can see both hard drives and it is labeled /hdb5 I believe.  Is there anyway I can make my old XP hard drive seeable by my Ubuntu system so I can mount it and get important files off of it.

Thanks

---

### Post by divague on 2006-09-23
create a directory in /media, for example

sudo mkdir win

the edit your fstab

sudo gedit /etc/fstab

if your windows partition is a NTFS, add this line

/dev/hda5   /media/win   ntfs  defaults,nls=utf8,umask=007,gid=46 0     1

if it's a FAT32, then add this line

/dev/hda5   /media/win  vfat    defaults,utf8,umask=007,gid=46 0     1

save the fstab file, and in the terminal put:

sudo mount -a

---

