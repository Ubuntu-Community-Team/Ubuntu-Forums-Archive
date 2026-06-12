---
title: "Problems Mounting Ext3 in Kubuntu 8.10"
date: 2009-03-21
forum: General Help
---

### Post by psycho457 on 2009-03-21
I have an issue mounting an ext3 drive(sda1). This drive has been mounted without any problems in the past and I cannot recall doing anything which may have caused this problem. I have also attempted to mount sda1 in knoppix but without any success. 

Previously I have used Ext2 IFS driver in windows to read and write from/to sda1 without any problems. When I was unable to mount sda1 I could only read the drive from windows.

The error I have when mounting sda1 is "mount: unknown filesystem type 'ext4'". sda1 has not been formatted to ext4 and should still be ext3.

Summary of HD and OS configuration
80GB	ext3	sdc1	IDE	kubuntu 8.10 (swap also on this drive)
400GB	ntfs	sdb1	SATA	windows xp
1TB	ext3	sda1	SATA	no os installed (storage only) ** drive with mount issue **

Commands used to mount
```

>> sudo mount -t ext3 /dev/sda1 /media/Storage
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

>> dmesg | tail
[   45.985198] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   56.928016] eth1: no IPv6 routers present
[  157.092422] ppdev0: registered pardevice
[  157.140309] ppdev0: unregistered pardevice
[  159.752862] ppdev0: registered pardevice
[  159.800206] ppdev0: unregistered pardevice
[  159.849885] ppdev0: registered pardevice
[  159.896022] ppdev0: unregistered pardevice
[ 2506.099694] EXT3-fs: sda1: couldn't mount RDWR because of unsupported optional features (e00000).
[ 3184.878173] EXT3-fs: sda1: couldn't mount RDWR because of unsupported optional features (e00000).

```


Omitting filesystem type
```

>> sudo mount /dev/sda1 /media/Storage
mount: unknown filesystem type 'ext4'

```

Access for files in media
```

>>ls -l /media
total 8
lrwxrwxrwx 1 root root    6 2008-11-11 19:24 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-11-11 19:24 cdrom0
drwxrwsrwx 2 root root 4096 2009-03-20 22:59 Storage

```


My current kernel is
```

Linux comp 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

```
I did run sabayon with kernel version 2.6.28 and ext4 support and still unable to mount.

Running sudo fdisk -l produces 
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00043a6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001   83  Linux

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd0fbd0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c660c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris

```

I have some concerns with the file system features FEATURE_R21 FEATURE_R22 FEATURE_R23. Should these be there?

```

>>sudo tune2fs -l /dev/sda1

tune2fs 1.41.4 (27-Jan-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          25483298-0e85-493f-9a3d-d949a1fae275
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype sparse_super large_file FEATURE_R21 FEATURE_R22 FEATURE_R23
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              61054976
Block count:              244190000
Reserved block count:     12209500
Free blocks:              118845527
Free inodes:              60983032
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      965
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Wed Oct  1 08:33:37 2008
Last mount time:          Fri Mar 13 18:16:15 2009
Last write time:          Fri Mar 13 18:16:15 2009
Mount count:              282
Maximum mount count:      1
Last checked:             Wed Oct  1 08:33:37 2008
Check interval:           15552000 (6 months)
Next check after:         Mon Mar 30 08:33:37 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      f2fd157f-67a3-4433-a3a8-5dc27c906399
Journal backup:           inode blocks

```

I did attempt an an fsck with latest version of e2fsck
```

>> sudo fsck /dev/sda1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1 has unsupported feature(s): FEATURE_R21 FEATURE_R22 FEATURE_R23
e2fsck: Get a newer version of e2fsck!

```

Any ideas?
Thanks in advance.

---

### Post by psycho457 on 2009-03-24
Solution:
I used mke2fs to find an alternate superblock
```

sudo mke2fs -n /dev/sda1 

```

I got a list of alternate superblocks and chose 32768 to restore the superblock using
```

fsck -b 32768 /dev/sda1

```

All damaged blocks were restored and mount was successful.

See
[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

---

