---
title: "Mountinh a USB pen drive"
date: 2005-06-14
forum: Desktop Environments
---

### Post by python on 2005-06-14
Right, I've never had trouble with this before. I am using a test install of Warty on an old P2 233Mz machine. Runs fine. Not relevant.

#lsusb detects my pendrive, as does

#fdisk -l (comes back with sda1)


So, my fstab entry is:

```
/dev/sda1        /media/usb0        auto        rw,user         0        0
```

When I try to mount (#mount /dev/sda1 /media/usb0), it gives me the error "mount: you must specify the filesystem type.

I tried replacing "auto" with "vfat" (as #fdisk -l returns FAT16 as the filesystem type) to no avail.



HELP!

---

### Post by python on 2005-06-14
I fixed the problem. Easy. If anyone else has this problem, all you need to do is mount for the first time with "-t <filesystem>" (in my case "mount /dev/sda1 /media/usb0 -t vfat) and then you're fine.

---

### Post by levin on 2005-11-25
This is really helpful!! thanks a lot. Breezy has no problem on my VAIO. However, due to resources constraint, I tried changing Gnome to Xubuntu-desktop. As such, the auto usb pendrive mounting has gone in XFCE. Have been wondering around and guess what? This has made my day!! Thanks for the info.. =)

This is not all.. It is still unable to detect another of of my pendrive partition.. I am still working on it..

---

