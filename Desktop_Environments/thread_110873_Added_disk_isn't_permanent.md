---
title: "Added disk isn't permanent"
date: 2005-12-31
forum: Desktop Environments
---

### Post by popie on 2005-12-31
I moved a hard drive to my Ubuntu system from another system, and it isn't recognized properly after a reboot.

I physically installed the disk, then went to system, adminstration, disks and defined the mount point. The disk works great, but the mount point isn't there after a reboot.

How does one go about making this disk permanent? Is there a place to do this in the gui? I'm not a Linux expert, I've used Mandrake's disk tool, which looks similar to Ubuntu's and didn't require anything extra to make the disk permanent, thus my question.

Here's the fdisk -l report (hdb1 is the new disk in this system):
```
root@epox:/# fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            7110        7297     1510110    5  Extended
/dev/hda3            1217        7109    47335522+  83  Linux
/dev/hda5            7110        7297     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24321   195358401   83  Linux

```

---

### Post by everdred on 2005-12-31
You'll need to add a line to your /etc/fstab to have your drive auto-mounted at startup.

---

### Post by popie on 2005-12-31
[QUOTE=everdred]You'll need to add a line to your /etc/fstab to have your drive auto-mounted at startup.[/QUOTE]

Does this look correct? (new device, /dev/hdb1, still commented)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
#/dev/hdb1      /home/images    ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by popie on 2005-12-31
I meant to type it with my username included:

```
/dev/hdb1      /home/myuserid/images    ext3    defaults        0       2
```

---

