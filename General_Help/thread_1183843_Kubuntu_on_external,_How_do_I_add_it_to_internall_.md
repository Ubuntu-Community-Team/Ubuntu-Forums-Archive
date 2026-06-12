---
title: "Kubuntu on external, How do I add it to internall HDD's Grub?"
date: 2009-06-10
forum: General Help
---

### Post by gletob on 2009-06-10
Ok so I have Kubuntu on an external HDD.  When I was installing I unchecked the install boot loader and now I can't get to my kubuntu install from anywhere besides inside ubuntu.  Any help is appreciated.

sudo fdisk -l
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce06f85c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9371    75272526    7  HPFS/NTFS
/dev/sda2            9372       14593    41945715    5  Extended
/dev/sda5            9372       14331    39841137   83  Linux (Ubuntu internal HDD)
/dev/sda6           14332       14593     2104483+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ebf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              33        3280    26089560    5  Extended
/dev/sdb2            3281       38913   286222072+   7  HPFS/NTFS
/dev/sdb3   *           1          32      257008+  83  Linux (Kubuntu)
/dev/sdb5            3020        3280     2096451   82  Linux swap / Solaris
/dev/sdb6              33        3019    23993014+  83  Linux

Partition table entries are not in disk order
```

---

### Post by synapsys on 2009-06-10
You have to add an entry to grub to show it where your kubuntu installation is so that it knows how to boot it. Search these forums or google 'grub' for more info.

---

