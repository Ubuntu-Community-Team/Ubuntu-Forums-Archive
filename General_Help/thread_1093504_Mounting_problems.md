---
title: "Mounting problems"
date: 2009-03-11
forum: General Help
---

### Post by kiddd on 2009-03-11
Hello ! I have just one HDD with two partitions I created in WinXP ( one with the OS files and the second with my personal files and documents ).I then created a third partition ( ext3-primary ) and installed Ubuntu.Now , my question is : how can i setup this whole story in order to get Ubuntu understand I want it to auto-mount both partitions I have from WinXP ?

I've been trying to edit the /etc/fstab myself but I can't make it on my own.

sudo fdisk -l

#
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77757775

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3218    25848553+   7  HPFS/NTFS
/dev/sda2            3219       27851   197864572+   f  W95 Ext'd (LBA)
/dev/sda3           27852       30401    20482875   83  Linux
/dev/sda5            3219       27851   197864541    7  HPFS/NTFS

#

gksudo gedit /etc/fstab

#
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec,utf8 0       0
#

---

### Post by taurus on 2009-03-11
Just install ntfs-config and use it to configure your ntfs partitions.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by kiddd on 2009-03-11
> **taurus said:**
> Just install ntfs-config and use it to configure your ntfs partitions.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```


Great ! it works just perfect ! ehh...one more thing , how do you post using that square  ---CODE--- ? Thanks man !

---

### Post by mhgsys on 2009-03-11
> **kiddd said:**
> Great ! it works just perfect ! ehh...one more thing , how do you post using that square  ---CODE--- ? Thanks man !

lol

you just press qoute

lol, 

ohw, that's not what you ment.

---

### Post by bodhi.zazen on 2009-03-11
[noparse]```
some commands here
```[/noparse]

Yields 

```
some commands here
```and

[noparse]> some quote here[/noparse]

Yields

> some quote here

---

### Post by mhgsys on 2009-03-11
@bodhi-zazen
```


Thanks alot.


```

---

