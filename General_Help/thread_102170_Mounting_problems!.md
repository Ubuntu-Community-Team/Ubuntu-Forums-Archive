---
title: "Mounting problems!"
date: 2005-12-11
forum: General Help
---

### Post by monkeyface on 2005-12-11
When I put a usbdisk or a cdrom into my computer, it gets mounted in /media/usbdisk or cdrom0 automatic, but not in nautilus, and when I try to mount or open it, nautilus says that it couldn't find a mounting point for /dev/hdc, /dev/sdb1 or whatever it is called...
I think this sounds like HAL is mounting the devices before gnome can detect them, but I don't know how to disable hald.

My kernel is 2.6.14 with ck patchset version 6 (with all usb support compiled IN kernel).
I haven't tried the stock kernels.

My fstab looks like this:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    noatime,errors=remount-ro 0       1
/dev/sda1       /boot           ext2    noatime         0       2
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   auto    ro,user,noauto,unhide     0       0
/dev/hdd        /media/cdrom1   auto    ro,user,noauto,unhide     0       0
/dev/fd0        /media/floppy   auto    rw,user,noauto  0       0

---

