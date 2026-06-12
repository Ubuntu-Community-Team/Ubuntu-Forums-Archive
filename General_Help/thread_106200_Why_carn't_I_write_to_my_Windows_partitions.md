---
title: "Why carn't I write to my Windows partitions?"
date: 2005-12-20
forum: General Help
---

### Post by ngms27 on 2005-12-20
On bootup breezy appears to mount my Windows partitions as rw. However I cannot write to them as if comes up with permission denied.

These are FAT32 partitions.

Any ideas?

---

### Post by frodon on 2005-12-20
Could you post your fstab file please ? : ```
sudo gedit /etc/fstab
```

---

### Post by Domie on 2005-12-20
[QUOTE=ngms27]On bootup breezy appears to mount my Windows partitions as rw. However I cannot write to them as if comes up with permission denied.

These are FAT32 partitions.

Any ideas?[/QUOTE]

Use a umask option in /etc/fstab

It should be something like this:

/dev/hda1 /media/hda1 vfat defaults,umask=0000 0 0

Or another option if you want some restrictions. Just remember to use umask=0XXX where XXX is the opposite of chmod.

---

### Post by codejunkie on 2005-12-20
[QUOTE=ngms27]On bootup breezy appears to mount my Windows partitions as rw. However I cannot write to them as if comes up with permission denied.

These are FAT32 partitions.

Any ideas?[/QUOTE]
i have noticed a couple of times, installing breezy if the installer automaticly detects and mount's my fat32 windows partition, it sets it up as read only in the /etc/fstab file for some reason. i have to change the entry manualy to get it to work this guide will help you with that [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat) hope this helps.

---

### Post by ngms27 on 2005-12-20
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda7       /media/hda7     ext2    defaults        0       2
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by frodon on 2005-12-20
Modify your file like that : ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda9 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 vfat **iocharset=utf8,rw,user,umask=000** 0 0
/dev/hda5 /media/hda5 vfat **iocharset=utf8,rw,user,umask=000** 0 0
/dev/hda6 /media/hda6 vfat **iocharset=utf8,rw,user,umask=000** 0 0
/dev/hda7 /media/hda7 ext2 defaults 0 2
/dev/hda8 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```Then do a "sudo mount -a" or reboot.

Here are some explainations of the options if you want to understand what you do : [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

