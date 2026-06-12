---
title: "Wierd permissions problem"
date: 2006-01-09
forum: General Help
---

### Post by ngms27 on 2006-01-09
For some reason I'm intermittantly unable to write to HDB1 and other drives despite them being mounted as rw. For example I created loads of files using BitTornado and when trying to resume the files I get unable to write.

If I try and manually create a file or directory I get the same problem.

Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    iocharset=utf8,rw,user,umask=000 0 0
/dev/hda5       /media/hda5     vfat    iocharset=utf8,rw,user,umask=000 0 0
/dev/hda6       /media/hda6     vfat    iocharset=utf8,rw,user,umask=000 0 0
/dev/hda7       /media/hda7     ext2    defaults        0       2
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/hdb1     vfat    iocharset=utf8,rw,user,umask=000 0 0
/dev/hdb2       /media/hdb2     vfat    iocharset=utf8,rw,user,umask=000 0 0
/dev/hdb3       /media/hdb3     ext3    defaults,errors=remount-ro 0       2
/dev/hdb4       /media/hdb4     ext3    defaults,errors=remount-ro 0       3

Here are my mount point permissions etc

lrwxrwxrwx   1 root root     6 2005-10-15 16:03 cdrom -> cdrom0
drwxr-xr-x   2 root root  4096 2005-10-15 16:03 cdrom0
drwxrwxrwx  23 root root  8192 1970-01-01 01:00 hda1
drwxrwxrwx  28 root root 32768 1970-01-01 01:00 hda5
drwxrwxrwx  30 root root 32768 1970-01-01 01:00 hda6
drwxr-xr-x  22 root root  4096 2005-10-21 08:01 hda7
drwxrwxrwx   7 root root 16384 1970-01-01 01:00 hdb1
drwxrwxrwx   4 root root 16384 1970-01-01 01:00 hdb2
drwxr-xr-x   3 root root  4096 2005-12-29 16:39 hdb3
drwxr-xr-x   3 root root  4096 2005-12-29 16:44 hdb4

Any ideas?

Thanks

JonnyT

---

### Post by aysiu on 2006-01-09
[QUOTE=ngms27]
/dev/hdb1       /media/hdb1     vfat    iocharset=utf8,rw,user,umask=000 0 0[/QUOTE] I don't know if this makes a difference, but try replacing your line with this line ```
/dev/hdb1       /media/hdb1     vfat    iocharset=utf8,umask=000 0 0
``` and reboot your computer. Any luck?

---

### Post by ngms27 on 2006-01-09
As per another thread I carried out error checking with automatic fix within Windows and the problem seems to have gone away for now.

I'm still thinking your solution could work as FAT32 partitions don't have permissions so it could well be the mounting thats causing the problem.

However like others I have noticed that on a reboot you can write to the partition and the read only seems to kick in a few minutes after booting which is really strange.

Are there any timed background processes that could do this?

JonnyT

---

