---
title: "Cannot read mounted ntfs partition or more than one fat32 volume"
date: 2006-09-16
forum: Desktop Environments
---

### Post by don_m on 2006-09-16
I have Ubuntu 6.06 installed on a deskstop. The install is on one 40GB drive with 4 partitions.

My fstab file is as follows:

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
/dev/hda6    /media/windows vfat  iocharset=utf8,umask=000  0    0
/dev/hda5    /media/windows vfat  iocharset=utf8,umask=000  0    0
[/I]

If I switch the last two lines, hda6 and hda5, the last one will appear on the deskstop. 

I cannot see the hda1 ntfs partition either; I only want to read from hda5 ntfs.

The cdrom and the other linux partitions are accessbile with no problems. Memory cards with card reader function properly. A look at System->Adminstration-Disks tells me that the partitions are enabled. A look under /media/windows only pulls up the last line. Again, hda1 and hda6 are not present under /media/windows.

Can someone tell me why I am not able read hda1 and hda6?

---

### Post by don_m on 2006-09-17
[http://www.linuxforums.org/forum/371118-post2.html](http://www.linuxforums.org/forum/371118-post2.html)


Quote:Originally Posted by don_m
Can someone tell me why I am not able read hda1 and hda6?

It's because you are trying to mount them all in the same directory.
If you want to have them all mounted at the same time, you need to mount them in separate directories. Since you already have one (/media/windows), create additional two directories and change fstab file to mount the other two partitions in those directories.

For example, create directories "windows2" and "windows3":

Code:
mkdir /media/{windows2,windows3}

and change corresponding lines in fstab file to use those directories:

Code:
/dev/hda1 /media/windows2 -t ntfs -o nls=utf8,umask=0222
/dev/hda6 /media/windows3 vfat iocharset=utf8,umask=000 0 0

---

