---
title: "One Partition not found."
date: 2006-08-03
forum: Desktop Environments
---

### Post by tamarku on 2006-08-03
OK, I know this is probably a simple problem but I cannot figure this one out.  I have 2 Hardrives. I am dual booting with GRUB, PCLOS and UBUNTU 6.06.  PCLOS is installed on my 2nd HDD in hdb1.  I have 2 other partitions (I thought FAT32), one holds a bunch of movies, music, jpegs, Linux themes; all kinds of stuff.  I wanted to use the other partition for my backups.  The one partition I have no problems mounting and listening to music.  But this other partition will not mount at all.  Here is a screenshot of my DiskManager: 
[http://img.photobucket.com/albums/v285/tamarku/DiskManager.png](http://img.photobucket.com/albums/v285/tamarku/DiskManager.png)

Here is my fstab: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb5	/media/storage	vfat	iocharset=utf8,umask=0000	0	0
/dev/hdb3	/media/extra	vfat	iocharset=utf8,umask=0000	0	0


It is the /dev/hdb3 partition I am trying to work with.  Any ideas would be greatly appreciated. 

Thanks.

---

### Post by OpsVentus on 2006-08-04
Can you try to remove the last line from your fstab. The one starting with "/dev/hdb3".
Then start disk manager again and look what it says about the disk then.
If it's the same try GParted to look at the disk.

Cheers,
Bart.

---

