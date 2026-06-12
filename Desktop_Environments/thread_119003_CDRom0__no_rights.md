---
title: "CDRom0  no rights ?"
date: 2006-01-18
forum: Desktop Environments
---

### Post by Dutch on 2006-01-18
Hi I looked at this forum but I can't find out what's the problem.
My Cdrom0 wil not open when I push the open buttun
Also ifI start CDRomplayer, it says u seem to have no rights.

In the terminal I said:

mount /dev/cdrom

the etc/fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0


```

like to hear from u.

---

### Post by lha on 2006-01-19
Don't know nothin'bout CDRomplayer, but

You have to u(n)mount cd before you get it out.
```
umount /media/cdrom0
```

---

### Post by Zalbor on 2006-01-19
For unmounting and ejecting, you can just right-click on the cdrom's icon and choose eject.

---

