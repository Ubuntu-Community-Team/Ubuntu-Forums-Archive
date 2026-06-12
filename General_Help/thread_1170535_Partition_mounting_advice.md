---
title: "Partition mounting advice"
date: 2009-05-26
forum: General Help
---

### Post by Hubster on 2009-05-26
Hello,

Can you help me mount my drives correctly please, especially devSdb1 & devSdb5. The problem is that although I can access them fine manually, it's causing havoc with things like Amarok trying to rescan my entire collection every time I relog, or stopping my desk top short cuts I create from working for example.

Any advice on sorting out this mess gratefully received :D

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=55562271-66c9-4f96-9819-5d32907072e9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c331b65e-6bd2-4caa-a07d-dba092889b1c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f347f34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14907   119740446    7  HPFS/NTFS
/dev/sda2           14908       60801   368643555    f  W95 Ext'd (LBA)
/dev/sda5           28282       60801   261216868+  83  Linux
/dev/sda6           14908       27732   103016749+  83  Linux
/dev/sda7           27733       28281     4409811   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00099e0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       63741   511999551    7  HPFS/NTFS
/dev/sdb2           63742      121601   464760450    5  Extended
/dev/sdb5           63742      121601   464760418+  83  Linux


```

---

### Post by drs305 on 2009-05-26
You can add the following two lines in fstab, with modifications. Of course, change the *username* and *mountpoints* for your setup.

```

/dev/sdb1 */media/mountpoint* ntfs-3g auto,users,uid=1000,umask=027,utf8 0 0
/dev/sdb5 */media/mountpoint* ext3 auto,users,relatime 0 2

```

Your mount point might be /media or /mnt, depending on how you have it set up. Generally removable drives are put in /media, but it's really up to your preferences.

Make sure the mount points exist and are owned by you. Ownership is especially important for the ext3 folder.

I prefer UUIDs or labels for the device IDs since they will not normally change. To get the UUIDs, run:
```

sudo blkid -c /dev/null

```
Once you have the correct UUID, replace "/dev/sdXX" with "UUID=" and the UUID. A typical fstab entry with a UUID would be:
> 
UUID=40c00255-22b3-488b-ae7e-9dbe4e2beac7 /media/mydata ext3  relatime,uid=1000,auto 0 2


Once you have made the fstab changes, you can run "sudo umount -a" (disregard the busy messages) and "sudo mount -a". If you get no error messages, everything worked.

---

### Post by Hubster on 2009-05-26
I'll give it a go

Thanks mate

---

