---
title: "Regain access to Partitions?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by bruder_s on 2006-07-11
Hi,

yesterday, I installed fuse to access a ntfs-partition in rw-mode.
It works for one partition, but I can't mount my other ntfs-partitions (hdb1 and hdb2) anymore.
I found out the nodes in /dev are missing, so I tried to set them up again.
I guess I did this step wrong because all the devices have root:disk as owner and the two I manually added have root:root.
Maybe udev is the problem, because I had to manually do some mknod (can't find it anymore)...

Here's what I did:

```
root@peroni:/mnt# ls -all
insgesamt 20
drwxr-xr-x  5 root root 4096 2006-07-09 14:59 .
drwxr-xr-x 22 root root 4096 2006-07-05 22:35 ..
drwxr-xr-x  2 root root 4096 2006-07-09 14:59 eigene_dateien
drwxr-xr-x  2 root root 4096 2006-07-09 14:58 musik
drwxr-xr-x  2 root root 4096 2006-07-09 14:58 win
root@peroni:/mnt# fdisk -l /dev/hdb

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/hdb2            5101       19457   115322602+   7  HPFS/NTFS
root@peroni:/mnt# mount -t ntfs /dev/hdb1 /mnt/win
mount: special device /dev/hdb1 does not exist
root@peroni:/mnt# mount -t ntfs /dev/hdb2 /mnt/musik
mount: special device /dev/hdb2 does not exist
root@peroni:/mnt# ls -all /dev/hd*
brw-rw---- 1 root disk   3,  0 2006-07-11 01:33 /dev/hda
brw-rw---- 1 root disk   3,  1 2006-07-11 01:33 /dev/hda1
brw-rw---- 1 root disk   3,  2 2006-07-11 01:33 /dev/hda2
brw-rw---- 1 root disk   3,  5 2006-07-11 01:33 /dev/hda5
brw-rw---- 1 root disk   3, 64 2006-07-11 01:33 /dev/hdb
brw-rw---- 1 root cdrom 22,  0 2006-07-11 01:33 /dev/hdc
brw-rw---- 1 root disk  22, 64 2006-07-11 01:33 /dev/hdd
brw-rw---- 1 root disk  22, 65 2006-07-11 01:33 /dev/hdd1
root@peroni:/mnt# mknod -m 660 /dev/hdb1 b 3 65
root@peroni:/mnt# mknod -m 660 /dev/hdb2 b 3 66
root@peroni:/mnt# ls -all /dev/hd*
brw-rw---- 1 root disk   3,  0 2006-07-11 01:33 /dev/hda
brw-rw---- 1 root disk   3,  1 2006-07-11 01:33 /dev/hda1
brw-rw---- 1 root disk   3,  2 2006-07-11 01:33 /dev/hda2
brw-rw---- 1 root disk   3,  5 2006-07-11 01:33 /dev/hda5
brw-rw---- 1 root disk   3, 64 2006-07-11 01:33 /dev/hdb
brw-rw---- 1 root root   3, 65 2006-07-11 21:21 /dev/hdb1
brw-rw---- 1 root root   3, 66 2006-07-11 21:22 /dev/hdb2
brw-rw---- 1 root cdrom 22,  0 2006-07-11 01:33 /dev/hdc
brw-rw---- 1 root disk  22, 64 2006-07-11 01:33 /dev/hdd
brw-rw---- 1 root disk  22, 65 2006-07-11 01:33 /dev/hdd1
root@peroni:/mnt# mount -t ntfs /dev/hdb1 /mnt/win
mount: /dev/hdb1 is not a valid block device
root@peroni:/mnt# mount -t ntfs /dev/hdb2 /mnt/musik
mount: /dev/hdb2 is not a valid block device
root@peroni:/mnt#
```

Maybe someone can help me with this...

Thanks in advance

---

