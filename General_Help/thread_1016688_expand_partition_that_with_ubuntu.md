---
title: "expand partition that with ubuntu"
date: 2008-12-20
forum: General Help
---

### Post by demiscy on 2008-12-20
my laptop hard disk is 260GB and i have installed windows vista and ubuntu. when i installed ubuntu it was just to try it so i only shrink the vista partition by 30GB and installed ubuntu on that 30GB. now that i like ubuntu and want to transfer alot of files to ubuntu i want to shrink the vista partition to 100GB(i know how with vista) and expand the ubuntu partition to another 100GB and i would like some help please on how to do it usung ubuntu...

---

### Post by taurus on 2008-12-20
If root filesystem (/) is next to vista, then that would be fine to resize the partitions.  

What is the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

You can use gparted from the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), to shrink vista's partition and expand Ubuntu's partition.  Of course, _always_ back up your files first before you resizing anything.

---

### Post by demiscy on 2008-12-20
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b43cf26

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       26322   209892352    7  HPFS/NTFS
/dev/sda3           26323       30227    31366912+  83  Linux
/dev/sda4           30228       30401     1397655    5  Extended
/dev/sda5           30228       30401     1397623+  82  Linux swap / Solaris


this is the output of that command

---

