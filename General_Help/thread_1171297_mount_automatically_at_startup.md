---
title: "mount automatically at startup"
date: 2009-05-27
forum: General Help
---

### Post by shivam89 on 2009-05-27
how can i make all my disk partitions to mount automatically at startup

---

### Post by JohnB-nbr on 2009-05-27
shivam89,

I suggest you to read [this page]("https://help.ubuntu.com/community/Fstab"). You will find what you need.

---

### Post by x33a on 2009-05-27
post the output of
```
cat /etc/fstab
```

---

### Post by shivam89 on 2009-05-28
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=9d15a61d-8b2d-4a73-ae6d-cdcfe9d84436 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by x33a on 2009-05-28
please post the output of
```
sudo fdisk -l
```

---

### Post by shivam89 on 2009-05-29
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x271a271a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865       19456   117210240    f  W95 Ext'd (LBA)
/dev/sda5            4865        9728    39070048+   7  HPFS/NTFS
/dev/sda6            9729       10973    10000431    7  HPFS/NTFS
/dev/sda7           14593       19456    39070048+   7  HPFS/NTFS
/dev/sda8           10974       14592    29069586   83  Linux

---

### Post by x33a on 2009-05-29
download ntfs-3g and ntfs-config.

```
sudo aptitude install ntfs-3g ntfs-config
```

after that go to system -> administration -> ntfs configuration tool.

select the partitions you want to manage, and they'll be automatically mounted at startup from the next boot.

---

