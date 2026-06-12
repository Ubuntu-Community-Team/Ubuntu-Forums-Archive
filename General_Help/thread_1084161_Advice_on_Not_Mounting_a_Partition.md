---
title: "Advice on Not Mounting a Partition"
date: 2009-03-01
forum: General Help
---

### Post by CaesarLike on 2009-03-01
HI there,

I have a pc that dual boots with XP.  Both Ubuntu and XP are on the  same disk.  I would like it so that the windows partition cannot be mounted via Nautilus.  I know I can set the partition and its mount point for root access only, and this would stop a user from mounting the partition.  However, can I set fstab or some other setting to not show the partition in Nautilus?  The Ubuntu setup has a single account, so the user in question has an Admin account.

---

### Post by DGortze380 on 2009-03-01
> **CaesarLike said:**
> HI there,

I have a pc that dual boots with XP.  Both Ubuntu and XP are on the  same disk.  I would like it so that the windows partition cannot be mounted via Nautilus.  I know I can set the partition and its mount point for root access only, and this would stop a user from mounting the partition.  However, can I set fstab or some other setting to not show the partition in Nautilus?  The Ubuntu setup has a single account, so the user in question has an Admin account.

Well, post the output of the following two commands

cat /etc/fstab
fdisk -l

It should be as simple as removing a line from fstab.

You need root access to use the mount command, so if it doesn't auto mount, and the user doesn't have sudo access to the mount command, you're all set.

---

### Post by CaesarLike on 2009-03-02
Thanks DGortze380.

Here is the fstab and fdisk -l output. I have added in brackets what each of the partitions is used for in the fdisk      output. While fstab shows only the linux related partitions, so it appears that neither of the 2 NTFS partitions that are also on the disk are being auto mounted.


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b37ff0e3-244e-42ff-a410-70702b3b2ec7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=7e0c162f-1c2d-4208-a467-1fd072f973e7 /home           ext3    relatime        0       2
# /dev/sda5
UUID=18d815a4-4ff0-4b2b-9631-de9cf566a886 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



> root@Solar2:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000558b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         914     7341673+  83  Linux  (Ubuntu File System Partition)
/dev/sda2   *         915        6136    41945715    7  HPFS/NTFS  (XP Install Partition)
/dev/sda3            6137       37074   248509485    7  HPFS/NTFS  (Shared NTFS Partition)
/dev/sda4           37075       38913    14771767+   5  Extended
/dev/sda5           37075       37596     4192933+  82  Linux swap / Solaris  (Linux Swap Partition)
/dev/sda6           37597       38913    10578771   83  Linux  (Ubuntu /home Partition)


The partition I want to restrict access to is /dev/sda2.  This is the XP install partition.  I notice this is not currently in fstab.  Yet the user can mount this using Nautilus without any problems.  I want to stop a user, even the admin user from mounting and accessing this partition to protect the XP install.  The /dev/sda3 partition is a second NTFS partition that both Ubuntu and XP can use to store and share files, so I need the user to be able to mount this in linux.

---

### Post by DGortze380 on 2009-03-02
> **CaesarLike said:**
> Thanks DGortze380.
I want to stop a user, even the admin user from mounting and accessing this partition to protect the XP install.  The /dev/sda3 partition is a second NTFS partition that both Ubuntu and XP can use to store and share files, so I need the user to be able to mount this in linux.


Well, you can't stop the 'admin' from mounting a partition. If you have root privileges, you can do whatever you want.

So my suggestion is this, adjust your access policies to follow some basic security rules... Rule #1 Limit Access To Necessary Files/Devices

I would create a new user account, with limited rights on the system. Only allow access to what is need. You won't 'restrict' the mount command, you just won't grant access to it. You can allow access to other 'admin' privileges through sudoers and groups as needed.

You need to maintain an 'admin' account (account with root privileges) for various reasons.

---

### Post by CaesarLike on 2009-03-03
Thanks DGortze380 for the reply. Your suggestion about using groups is a good idea.  Do you happen to know which group controls the ability to mount partitions?  I would still need the owners of the pc to be able to update the linux install, so they would definately need some admin abilities.

---

