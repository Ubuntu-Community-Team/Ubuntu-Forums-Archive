---
title: "Ubuntu won't detect external HDD"
date: 2006-08-31
forum: Desktop Environments
---

### Post by markcholden on 2006-08-31
I just installed Ubuntu a few days ago. I have an external HDD that contains a bunch of media and backup files. It worked just fine initially, but now it won't display or detect it. I tried "mount /dev/sdb1", which is where it used to be, but it tells me the device doesn't exist. I tried restarting the HDD. No success. Does anybody have any ideas?

Thanks.

---

### Post by Jussi Kukkonen on 2006-08-31
*sudo fdisk -l* will show mountable devices

---

### Post by markcholden on 2006-09-01
Ok...here's the output:

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       10751    86301180    7  HPFS/NTFS
/dev/sda3           11647       12161     4136737+  db  CP/M / CTOS / ...
/dev/sda4           10752       11646     7189087+   f  W95 Ext'd (LBA)
/dev/sda5           10752       11448     5598621   83  Linux
/dev/sda6           11449       11646     1590403+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?           1       38913   312568641    7  HPFS/NTFS
```

sdb is the device I'm trying to get to work. It works fine in Windows.

Thanks for the help.

---

### Post by markcholden on 2006-09-01
Also, when I do a "mount -t ntfs /dev/sdb1", it says "special device /dev/sdb1 does not exist".

---

### Post by Jussi Kukkonen on 2006-09-01
Since pmount (the fully automatic mounter Gnome uses) is failing there's probably something wrong, but...

> Also, when I do a "mount -t ntfs /dev/sdb1", it says "special device /dev/sdb1 does not exist".
Sounds odd, but if you haven't added a line into /etc/fstab, you need to mention the mount point too:
```
sudo mount -t ntfs /dev/sdb1 /media/windisk
```
/media/windisk needs to exist already.

---

### Post by markcholden on 2006-09-01
The mount point does already exist, and the line is there in /etc/fstab...:confused:

---

### Post by markcholden on 2006-09-01
I'm wondering what

> This doesn't look like a partition table
Probably you selected the wrong device.

in the output of "sudo fdisk -l" means.

---

### Post by Jussi Kukkonen on 2006-09-02
I was going to answer that it's mostly harmless -- believeing it was a result of not partitioning, but using the whole device as a partition. I checked and actually the message would be this in that case:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

```

So there probably is something wrong with the partition table...

---

