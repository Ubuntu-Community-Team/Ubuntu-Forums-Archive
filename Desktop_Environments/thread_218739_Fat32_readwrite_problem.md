---
title: "Fat32 read/write problem"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Bonez56 on 2006-07-19
Hi there,

I have 2x FAT32 partitions mounted on my PC, and both can be read/written using a terminal/console.

However, when using nautilus or thunar in Gnome, one of the partitions appears as read only. The other, is perfectly fine and I can read/write to it.

Here's a copy of my fstab file:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0 1
/dev/hda5       /home   ext3    nodev,nosuid 0 2
/dev/hda1       /usr    ext3    nodev 0 2
/dev/hda4       none            swap    sw              0  0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0  0
/dev/hdb1      /media/e    vfat codepage=850,iocharset=iso8859-1,umask=0 0 0
/dev/hda6      /media/d    vfat  codepage=850,iocharset=iso8859-1,umask=0 0 0

```

The one I am having problems with is /dev/hda6 which mounts to /media/d

however, /dev/hdb1 (or /media/e) works fine, both read and write using nautilus.

Can anyone shed some light on this? I've been searching for an answer for ages, but can't seem to find out what i'm doing wrong. 

I have an idea it's some kind of permissions problem, but just don't know where to start.

Thanks
Bonez

---

### Post by arcejorge on 2006-07-19
Hi, i think i had the same problem, i just added my uid and gid to /etc/fstab

like this

/dev/hda6      /media/d    vfat defaults,rw,user,gid=1000,uid=1000 0 0

and that worked

hope this helps

---

