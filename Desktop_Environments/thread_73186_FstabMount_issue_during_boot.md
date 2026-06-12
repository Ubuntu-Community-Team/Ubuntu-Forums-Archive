---
title: "Fstab/Mount issue during boot"
date: 2005-10-08
forum: Desktop Environments
---

### Post by oneybm on 2005-10-08
I added my two Win partitions to my fstab.  The NTFS works great; however, the fat32 partition doesn't.  During boot I just saw an error stating, UTF8 is not a valid character set for vfat.  The verbage may not be exact but that is most of it.  It also said that the filesystem will be case sensitive.  Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb1       /media/windows2 vfat    iocharset=utf8,umask=000   0       01

```

As usual 'preciate it...

---

### Post by Pablo_Escobar on 2005-10-08
/dev/hdb1       /media/windows2 vfat    iocharset=utf8,umask=000   0       01

Case sensitive message is a normal one,
You should loose the 1 at the end of that line, it should end with "0    0". Maybe it's causing problems :)

---

### Post by aysiu on 2005-10-08
[QUOTE=oneybm]During boot I just saw an error stating, UTF8 is not a valid character set for vfat.  The verbage may not be exact but that is most of it.  It also said that the filesystem will be case sensitive.[/QUOTE] I get that warning all the time. My FAT32 partition still mounts just fine, and I've never encountered any problems.

---

### Post by mlomker on 2005-10-08
I think Pablo is right.  I have a little [write-up here.]("http://ubuntuforums.org/showpost.php?p=355988&postcount=8")

---

