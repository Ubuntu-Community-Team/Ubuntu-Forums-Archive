---
title: "I submit defeat with my data unless ..."
date: 2009-05-23
forum: General Help
---

### Post by hart02 on 2009-05-23
I have a big problem that needs resolving. I cant find answers anywhere for it.unless this is solved I submit failure.

I have a drive formatted in ufs originally from my freenas install. Now i have ubuntu server with ufs support.
Any kind of mount variation gives me
```
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``` 

I type what it says to do and i get this

```
brian@bmansserver:~$ dmesg | tail 
[ 1042.679152] UFSD (fs/ufs/super.c, 336): ufs_parse_options:ENTER
[ 1042.679157] UFSD (fs/ufs/super.c, 702): ufs_fill_super:ufstype=ufs2
[ 1042.680139] ufs_read_super: bad magic number
[ 1042.680144] UFSD (fs/ufs/super.c, 1102): ufs_fill_super:EXIT (FAILED)
[ 1116.273385] UFSD (fs/ufs/super.c, 645): ufs_fill_super:ENTER
[ 1116.273390] UFSD (fs/ufs/super.c, 652): ufs_fill_super:flag 1
[ 1116.273394] UFSD (fs/ufs/super.c, 336): ufs_parse_options:ENTER
[ 1116.273400] UFSD (fs/ufs/super.c, 702): ufs_fill_super:ufstype=ufs2
[ 1116.277409] ufs_read_super: bad magic number
[ 1116.277413] UFSD (fs/ufs/super.c, 1102): ufs_fill_super:EXIT (FAILED)
```

I cannot find anything on Google. If anyone knows how to solve or where to find straight answers. I would be forever grateful.
Otherwise I could not live with myself.

---

### Post by oldos2er on 2009-05-23
Have you tried running fsck.ufs on the drive?

---

### Post by cariboo on 2009-05-23
Have you tried the following command?

```
mount -r -t ufs -o ufstype=ufs2 <device> <mount_dir>
```

I've used it sucessfully to mount ufs partition while running Jaunty.

---

### Post by hart02 on 2009-05-23
I get this
```
root@bmansserver:/usr/src/linux-headers-2.6.29.1# mount -r -t ufs -o ufstype=ufs2 /dev/sdc /media/Extra
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

and fsck.ufs gets this

```
root@bmansserver:/usr/src/linux-headers-2.6.29.1# fsck.ufs /dev/sdc1
** /dev/sdc1
Cannot find file system superblock
```

---

### Post by Aped on 2009-05-23
Sounds silly, but are /dev/sdc and /media/Extra/ valid (existing, too;)? You might just want to double- and triple-check. 

I had the same issue, was just accidentally pointing to a typo, felt retarded when I finally saw what the problem was. 

Good luck.

---

### Post by hart02 on 2009-05-24
here is some output of some commands
```
root@bmansserver:/usr/src/linux-headers-2.6.29.1# fsck /dev/sdc1
fsck 1.41.4 (27-Jan-2009)
** /dev/sdc1
Cannot find file system superblock
root@bmansserver:/usr/src/linux-headers-2.6.29.1# fsck /dev/sdc
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@bmansserver:/usr/src/linux-headers-2.6.29.1# fsck.ufs /dev/sdc
** /dev/sdc
Cannot find file system superblock
root@bmansserver:/usr/src/linux-headers-2.6.29.1# dd if=/dev/sdc skip=32 of=/dev/sdc seek=16 bs=512 count=16
16+0 records in
16+0 records out
8192 bytes (8.2 kB) copied, 0.015088 s, 543 kB/s
root@bmansserver:/usr/src/linux-headers-2.6.29.1# mount -r -t ufs -o ufstype=ufs2 /dev/sdc1 /media/Extra
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@bmansserver:/usr/src/linux-headers-2.6.29.1# mount -r -t ufs -o ufstype=ufs2 /dev/sdc1 /media/disk-2
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@bmansserver:/usr/src/linux-headers-2.6.29.1# dmesg | tail
[31061.769796] UFSD (fs/ufs/super.c, 336): ufs_parse_options:ENTER
[31061.769802] UFSD (fs/ufs/super.c, 702): ufs_fill_super:ufstype=ufs2
[31061.791374] ufs_read_super: bad magic number
[31061.791380] UFSD (fs/ufs/super.c, 1102): ufs_fill_super:EXIT (FAILED)
[33079.973292] UFSD (fs/ufs/super.c, 645): ufs_fill_super:ENTER
[33079.973297] UFSD (fs/ufs/super.c, 652): ufs_fill_super:flag 1
[33079.973301] UFSD (fs/ufs/super.c, 336): ufs_parse_options:ENTER
[33079.973306] UFSD (fs/ufs/super.c, 702): ufs_fill_super:ufstype=ufs2
[33079.996699] ufs_read_super: bad magic number
[33079.996705] UFSD (fs/ufs/super.c, 1102): ufs_fill_super:EXIT (FAILED)
root@bmansserver:/usr/src/linux-headers-2.6.29.1# ls /media
Brian  cdrom  cdrom0  disk  disk-2  disk-3  Extra
root@bmansserver:/usr/src/linux-headers-2.6.29.1# 

```
Nothing as you can see here. the partition is /dev/sdc1

---

### Post by hart02 on 2009-05-24
Ok this is assinine. I give up unless unless 
I know these entries look right
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=34378a70-ce05-4149-97d5-2de6fb9c8d17 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7eb1481e-8cd0-4f4c-aeaa-6a8416593e22 none            swap    sw              0       0
/dev/sdb1 /media/disk       ufs auto,ro,ufstype=ufs2,nodev,nosuid   0 0
/dev/sdc1  /media/Extra  ufs  auto,ro,ufstype=ufs2,nodev,nosuid  0  0
/dev/sdd1  /media/disk-3  ext3  user,suid,dev,exec  0  2
/dev/sde1  /media/Brian  ext3  user,suid,dev,exec  0  0

```

fdisk -l
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008fd31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3580    28756318+  83  Linux
/dev/sda2            3581        3739     1277167+   5  Extended
/dev/sda5            3581        3739     1277136   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 750.1 GB, 750156374016 bytes
256 heads, 63 sectors/track, 90845 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       90846   732574583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   a5  FreeBSD

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062126

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60616   486897988+  83  Linux
/dev/sdd2           60617       60801     1486012+   5  Extended
/dev/sdd5           60617       60801     1485981   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 750.1 GB, 750156374016 bytes
256 heads, 63 sectors/track, 90845 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       90846   732574583+  83  Linux

```

and i know /dev/sdb1 mount. so why wont /dev/sdc1?

---

