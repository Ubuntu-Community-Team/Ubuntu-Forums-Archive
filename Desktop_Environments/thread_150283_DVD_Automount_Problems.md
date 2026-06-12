---
title: "DVD Automount Problems"
date: 2006-03-25
forum: Desktop Environments
---

### Post by d351GuJu on 2006-03-25
Hey, Guys/gals

I need your help today after almost a year of using the greatest distro of all, kubuntu.  I am using Breezy 5.10 on KDE and I am having issues lately with automounting any kind of dvds.

Here's my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1       /boot           ext3    defaults        0       2
/dev/sda1	/media/windowsC	ntfs	nls=utf8,umask=0222	0	0
/dev/sda5	/media/windowsD	ntfs	nls=utf8,umask=0222	0	0
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hda        /media/cdrom   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

When I open up Storage Media under Konqueror, I see the drive but when I click on it after mounting it, it says "Could not enter folder /media/cdrom."

When I right click on that drive and go to properties, the ownership is listed as 400 and group as 401 with full access to owner and no access to other groups.

When I go under /media/cdrom folder the folder is locked because I do not have right to enter the folder due to its assigned to root only.  I do not know why this happens only if I insert any DVDs.  CDs work just fine!!!

Any help would really be appreciated!

Thanks,

d351GuJu  :mrgreen:

---

