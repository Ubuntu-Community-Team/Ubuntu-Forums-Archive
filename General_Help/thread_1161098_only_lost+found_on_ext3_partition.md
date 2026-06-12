---
title: "only lost+found on ext3 partition"
date: 2009-05-16
forum: General Help
---

### Post by CryFleuret on 2009-05-16
I had a GRUB error 17...I had a ext3 (with installed ubuntu 8.10) and a ntfs patrition ...I needed my system back quickly so I've formated the ntfs patrition as ext4 and I've instaled Ubuntu 9.04 on this patrition. The problem is with that old ext3 "/" patrition...I have some important files on this one...but when I mount the partition there is only "lost+found" folder...when I check the properties of this patrition I see that 175.5 GB of 195.2 GB is used...and many elements (files?) are detected...
Tried opening it with nautilus and midnight commander as root (with the option to see invisible files) and I still can't  see anything other than that damn "lost+found" folder...
gparted recognizes this partion correctly as ext3...

So...any ideas how can i get access to my files?

Fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=4c8d194e-c495-43f9-b846-d8a2d742553c /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=43de9c9a-c5db-48da-94bf-85c828ce6444 /boot           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=7bb33d1f-6145-46c5-aa4e-4f18b7ef63a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda6 /media/sda6 ext3 relatime,errors=remount-ro 0 1
```fdisc -l

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x441238a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         249     2000061   83  Linux
/dev/sda2             250       38913   310568580    5  Extended
/dev/sda5           38665       38913     2000092+  82  Linux swap / Solaris
/dev/sda6           12781       38663   207905134+  83  Linux
/dev/sda7             250       12780   100655194+  83  Linux

Partition table entries are not in disk order
```The partition I'm talking about is /dev/sda6

The partition was checked with fsck.

---

### Post by CryFleuret on 2009-05-16
Nevermind that...found everything in lost+found...

---

