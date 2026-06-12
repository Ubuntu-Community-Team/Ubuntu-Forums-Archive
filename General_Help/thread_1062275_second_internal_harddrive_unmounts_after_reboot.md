---
title: "second internal harddrive unmounts after reboot"
date: 2009-02-06
forum: General Help
---

### Post by composites on 2009-02-06
Every time I reboot, my second internal harddrive unmounts and I have to remount it with:
```
sudo mount /dev/sdb1 /home/public/2
```

I tried to follow [this thread](http://ubuntuforums.org/archive/index.php/t-980564.html) to resolve the problem to no avail.

[quote=sudo fdisk -l]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c3e61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120873   970912341   83  Linux
/dev/sda2          120874      121601     5847660    5  Extended
/dev/sda5          120874      121601     5847628+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00083706

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb01638b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3648    29302528+   7  HPFS/NTFS

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       91201   732572001    7  HPFS/NTFS[/quote]

[quote=sudo nano /etc/fstab]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b49eb232-60da-4fe4-a34d-1728229cbcd8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=332fec48-0ca6-4513-b4f5-4aff54bea882 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/quote]

[quote=sudo blkid /dev/sdb1]/dev/sdb1: UUID="108e1d08-bc00-43c0-b74c-fc8c5c87ffb7" SEC_TYPE="ext2" TYPE="ext3"[/quote]

//edit: fixed by adding:
```
# /dev/sdb1
UUID=108e1d08-bc00-43c0-b74c-fc8c5c87ffb7 /home/public/2 ext3 defaults,auto 0 2

```

---

