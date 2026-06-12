---
title: "Cant mount ntfs internal drive"
date: 2009-01-25
forum: General Help
---

### Post by devid on 2009-01-25
Just installed Ubuntu 8.04 from w2k adv server. I have three internal drives and I can't get the last one (sdc) to mount. 

Nautilus shows it as "SCSI Drive", and when i open it, it displays 'Unable to mount location. Can't mount file"

Followed directions on a site to add info to fstab

fdisk shows:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50acfa88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9553    76734441   83  Linux
/dev/sda2            9554        9729     1413720    5  Extended
/dev/sda5            9554        9729     1413688+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb68d521

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00b1356e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19929   160079661    7  HPFS/NTFS


----


fstab shows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=616c9272-09c2-44c6-92cc-036176c9ffdc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=897826e9-b8f6-4e3e-9cd5-0b51bf877267 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1 /media/f ntfs-3g defaults,nls=utf8,umask=007,guid=46 0 1  
/dev/sdb1 /media/g ntfs-3g defaults,nls=utf8,umask=007,guid=46 0 1 


the last two lines I added based on info from a site for mounting ntfs
I also created the /media/f and g directories.

---

one thing i noticed is that the device manager shows device type as ""storage", "block"" while the other working drives show "volume", "block". Is it possible that it thinks it's a cdrom, since it on the separate cable to the motherboard.  

thanks for any help.

---

### Post by sisco311 on 2009-01-25
Any error message if you try to mount it manually?
```
sudo mount /dev/sdc1 /media/f -t ntfs -o defaults,nls=utf8,umask=007,guid=46
```

---

### Post by taurus on 2009-01-25
See if you can at least mount one of them by hand from a terminal.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/g
df -h
```

---

### Post by devid on 2009-01-25
> **sisco311 said:**
> Any error message if you try to mount it manually?
```
sudo mount /dev/sdc1 /media/f -t ntfs -o defaults,nls=utf8,umask=007,guid=46
```

$ sudo mount /dev/sdc1 /media/f -t ntfs -o defaults,nls=utf8,umask=007,guid=46
[sudo] password for xxx: 
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
$ /sbin/mount.ntfs --help

ntfs-3g 1.2216 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2006-2008 Szabolcs Szakacsits
Copyright (C) 2005-2007 Yura Pakhuchiy

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro (read-only mount), force, remove_hiberfile, locale=,
          uid=, gid=, umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

---

### Post by devid on 2009-01-25
> **taurus said:**
> See if you can at least mount one of them by hand from a terminal.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/g
df -h
```

i changed to your command to try to mount the f, since g is already mounted. But f fails 

c$ sudo mount -t ntfs-3g /dev/sdc1 /media/f
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G  3.1G   66G   5% /
varrun                236M  220K  236M   1% /var/run
varlock               236M     0  236M   0% /var/lock
udev                  236M   52K  236M   1% /dev
devshm                236M   12K  236M   1% /dev/shm
/dev/sdb1             234G  204G   31G  87% /media/g

---

