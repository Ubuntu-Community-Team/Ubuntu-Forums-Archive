---
title: "RAID-1 /home on running system"
date: 2009-01-10
forum: General Help
---

### Post by szim90 on 2009-01-10
Hi everyone.

My current ubuntu install has two hard disks. Here is my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d1b404d1-d027-4f2d-afa7-811160768e0d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2f0a33da-4ab9-439b-b8ab-1a4fdb9ece59 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=fbe9afa9-d5e2-4350-80dd-433651bdfbb9	/home	ext3	defaults,relatime	0	2
#
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

I wanted to ask, if I purchase a third hard disk, it is possible to setup a raid-1 to just mirror the /home disk? I don't have anything critical on the system disk, so it does not need to be raided. Also, because it seemed relevant in the few guides I tried reading, there is only one partition on the /home disk, and all disks are SATA disks.

I apologize if this has already been answered - it appears all the howtos I read only cover backing up the entire root system, or adding raid during the ubuntu install.

Thank you for any help.

Regards,
szim90

---

