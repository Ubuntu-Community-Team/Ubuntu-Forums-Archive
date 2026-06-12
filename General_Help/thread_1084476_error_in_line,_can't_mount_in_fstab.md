---
title: "error in line, can't mount in fstab"
date: 2009-03-02
forum: General Help
---

### Post by guguma on 2009-03-02
I am trying to mount one of my partitions on boot using fstab, I created a mount point D under media and played with fstab my fstab looks like 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2fe76c42-77c4-4801-bf9c-ef09831a61cc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=81d93512-b080-4ec7-8ca8-5d4c5c354ddf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2       /media/D     fuseblk rw nosuid nodev user_id=0 group_id=0 allow_other blksize=4096
```

when I say 

```
sudo mount /dev/sda2 
```

I get 

```
 line 10 in /etc/fstab is bad
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
```

any help on this?

Also I used to use ntfs-3g before, I see that much has changed in 8.10 since I used Ubuntu.

What is the difference between fusebulk and ntfs-3g.

---

### Post by taurus on 2009-03-02
If /dev/sda2 is ntfs, why not make it simple like this in /etc/fstab

```
/dev/sda2    /media/D   ntfs-3g  defaults,locale=**en_US**.UTF-8  0  0
```
(if you are in the US--**en_US**).

---

