---
title: "can't access ntfs partition after gnome crash"
date: 2009-07-04
forum: Desktop Environments
---

### Post by agent-s on 2009-07-04
Gnome hung during startup once where I had to power off my laptop in order to reboot.  I lost a lot of Gnome settings which I was able to reconfigure but now I can't mount my ntfs partition.  It was removed from my fstab and I tried adding it again but to no avail.  Help!

---

### Post by theozzlives on 2009-07-04
can you still get into Windows? post the output of:```
fdisk -l
```

---

### Post by agent-s on 2009-07-04
Yes, I can still boot into Windows.

```
$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0779162

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        2575      200812+  83  Linux
/dev/sda3            2576        9364    54532642+  83  Linux
/dev/sda4            9365        9729     2931862+  82  Linux swap / Solaris

```

---

### Post by agent-s on 2009-07-09
```
~$ cat /proc/mounts 
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/disk/by-uuid/384371e4-01b3-47ac-b8b8-e0968560d24d / xfs rw,relatime,ikeep,noquota 0 0
/dev/disk/by-uuid/384371e4-01b3-47ac-b8b8-e0968560d24d /dev/.static/dev xfs rw,relatime,ikeep,noquota 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.24-24-generic/volatile tmpfs rw,relatime 0 0
tmpfs /dev/shm tmpfs rw,relatime 0 0
devpts /dev/pts devpts rw,relatime 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sda2 /boot ext3 rw,relatime,data=ordered 0 0
/dev/sda1 /mnt/windows fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0
securityfs /sys/kernel/security securityfs rw,relatime 0 0
gvfs-fuse-daemon /home/sapu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
/dev/sdb1 /media/SAPV3 fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0

```

---

### Post by agent-s on 2009-07-09
somehow it just works now after removing the fstab entry

---

