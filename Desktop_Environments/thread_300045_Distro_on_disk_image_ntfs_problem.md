---
title: "Distro on disk image ntfs problem"
date: 2006-11-15
forum: Desktop Environments
---

### Post by weakling on 2006-11-15
Hi I'm new here.:-D 

I made a disk image containing Kubuntu dapper and a customized initrd that will allow me to boot the disk image into a normal Kubuntu distro. The initrd will search for all disk partitions and look for the file dapper.img and boot from this image (mount using loopback and do the run-init stuff). My boot script can work on vfat, ntfs (using ntfs-3g), ext2 and ext3. All partition type works perfectly except ntfs.

Problem: On ntfs, the image will boot to the normal desktop without problem. Once I insert a USB disk, KDE will show me the dialog to mount the disk. If I accept the mount option, the whole partition changes to read-only. After that, I can no longer write to any folder. There is no problem using manual mount. :( 

I am guessing that this problem might be due to hal/udev. But I am not sure. Can someone show me where the system changes the mount type? Can it be an ntfs-3g problem (but I don't think it is)? :confused: 

BTW the disk image is simply a copy of the Kubuntu root file system, well except some folders that must be created independent of the base system such as /dev, /sys, /proc, etc.

Thanks! :)

---

### Post by weakling on 2006-11-15
After looking at /proc/mounts, I notice something that might help us find the problem. It is the disk image mounted using loop device that became read-only, the partition itself mounted via ntfs-3g is still rw.

Before:
/dev/loop0 / ext3 rw,data=ordered 0 0

After mounting usb flash disk in GUI:
/dev/loop0 / ext3 ro,data=ordered 0 0

Any ideas?

---

### Post by weakling on 2006-11-16
Solved it.

The filesystem on the disk image is badly damaged on the ntfs system.

---

