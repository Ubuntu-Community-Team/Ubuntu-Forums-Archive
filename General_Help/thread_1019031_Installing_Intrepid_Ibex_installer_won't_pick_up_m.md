---
title: "Installing Intrepid Ibex: installer won't pick up my partitions??"
date: 2008-12-22
forum: General Help
---

### Post by mark. on 2008-12-22
hello everyone and thanks in advance for your awesome help :D

so I have a 160gb hdd on my dell desktop thats currently partitioned into:
140gb windows
20gb feisty fawn <- broken completely, os unusable

I just got my intrepid ibex cd to install (to take over the 20gb 7.04) and when i get into the gparted part of the installer the hdd shows up as one, 160gb unallocated space :/ is there any way to fix this? i want to try linux again lol

---

### Post by dcstar on 2008-12-22
> **mark. said:**
> hello everyone and thanks in advance for your awesome help :D

so I have a 160gb hdd on my dell desktop thats currently partitioned into:
140gb windows
20gb feisty fawn <- broken completely, os unusable

I just got my intrepid ibex cd to install (to take over the 20gb 7.04) and when i get into the gparted part of the installer the hdd shows up as one, 160gb unallocated space :/ is there any way to fix this? i want to try linux again lol

Cancel the install, use the Live CD's Partition Editor to manually delete the old Linux partition, boot Windows to make sure that still works and then try the install again.

---

### Post by taurus on 2008-12-22
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mark. on 2008-12-22
fdisk -l shows:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1216d4fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17054   136986223+   7  HPFS/NTFS
/dev/sda2           17055       19457    19302097+   5  Extended
/dev/sda3           19270       19457     1510078+  82  Linux swap / Solaris
/dev/sda5           17055       19269    17791924+  83  Linux


p.s. gparted shows the hdd as one, unallocated drive as well :(

---

