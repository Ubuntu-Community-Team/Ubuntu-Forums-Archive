---
title: "floppy disk mounting"
date: 2009-03-20
forum: General Help
---

### Post by 123456789123456789123456 on 2009-03-20
I am wondering one thing, I have a customer that I will be building a computer for, with Ubuntu 8.10 or possible 9.04 if it comes out in time.  Any how, she wants a Floppy disk drive on the computer.  Her old computer has messed up, it was windows 95, and had a floppy drive.  If a floppy from that time with 95 should be readable and manageable with ubuntu, If she were to format a disk in ubuntu for gerneral use with her new computer only.  Would we have to mount the disk to a different mount point, or would the system do that automatically?

---

### Post by Rocket2DMn on 2009-03-20
The system should mount it automatically, and you can specify a mount point in /etc/fstab for it.

---

### Post by kanikilu on 2009-03-20
In 8.10 I had to add *floppy* to a new line in /etc/modules. Other than that, it should work fine mounting it to /media/floppy.

---

### Post by 123456789123456789123456 on 2009-03-20
what will that do, you can specify a mount point in /etc/fstab for it.
I have to admit, even though I understand mount points, I am not familure with fstab, or /etc/modules.

---

### Post by Rocket2DMn on 2009-03-20
Specifying a mount point in fstab will predetermine where a floppy drive mounts when you insert it into the drive.  For example, say you want it at /media/floppy
```
/dev/fd0  	/media/floppy  	auto  	rw,noauto,user,sync  	0 0
```
/dev/fd0 = the device
/media/floppy = the mount point
auto = the filesystem (floppies may be vfat, or ext2, etc, so we just use auto)
rw,noauto,user,sync = options (these can vary by preference)
0 0 = dump and check order (ignore these, just use 0s)

/etc/modules can be used to list kernel modules that load at system boot.  "floppy" is a module :)

---

