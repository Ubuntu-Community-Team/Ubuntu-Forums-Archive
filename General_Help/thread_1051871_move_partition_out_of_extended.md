---
title: "move partition out of extended"
date: 2009-01-27
forum: General Help
---

### Post by djbushido on 2009-01-27
I am wondering if it would be possible to move a partition from extended to primary. currently, ubuntu is installed in /dev/sdc5, which is an extended part of /dev/sdc2. I would like to move it from /sdc5 to /sdc2, so i don't have to size the extended partition and then it. any ideas?

---

### Post by caljohnsmith on 2009-01-27
How about first posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
To give a better idea of what the physical layout of your partitions is, and we can work from there if you want.

---

### Post by djbushido on 2009-01-27
Okay heres info:

fdisk:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9af30f7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156296384    78148161    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4fee4fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296384    78148161    7  HPFS/NTFS

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb8bbb8bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    56934359    28467148+  83  Linux
/dev/sdc2       116133885   117226304      546210   82  Linux swap / Solaris
/dev/sdc3        56934360   116133884    29599762+   5  Extended
/dev/sdc5        56934423   112969079    28017328+  83  Linux
/dev/sdc6       112969143   116133884     1582371   82  Linux swap / Solaris

Partition table entries are not in disk order

```

sfdisk (what is this?):
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=156296322, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=156296322, Id= 7, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size= 56934297, Id=83, bootable
/dev/sdc2 : start=116133885, size=  1092420, Id=82
/dev/sdc3 : start= 56934360, size= 59199525, Id= 5
/dev/sdc4 : start=        0, size=        0, Id= 0
/dev/sdc5 : start= 56934423, size= 56034657, Id=83
/dev/sdc6 : start=112969143, size=  3164742, Id=82

```

Any ideas?

---

### Post by caljohnsmith on 2009-01-27
One option would be to delete sdc2, and then convert your sdc5 logical partition into sdc2. That way you don't have to physically move any partitions around, you would simply be changing the partition table so that sdc5 would become sdc2. Is that maybe what you want to do? If so, I'm just curious, but why do you want to convert sdc5 into sdc2? What advantage are you looking for by converting sdc5 into a primary partition? Also I should mention that you have primary partition sdc4 open, so theoretically you could keep sdc2 and convert sdc5 into primary partition sdc4 if you wanted. But I can't think of any good reason off-hand to have two swap partitions on the same drive (unless you are using VirtualBox), so my vote would be to get rid of sdc2. Let me know what your goal is and we can work from there if you want.

---

### Post by djbushido on 2009-01-27
Okay, I agree on getting rid of sdc2, just didn't want to do that since i thought it was a container for sdc5 (thus deleting container AND partition AND valuable data). The two swap partitions was a partitioning error on my part. I dual-boot FC10 and Xubuntu, so had accidentally made 2 swap rather than updating /etc/fstab to use these. I previously hadn't wanted to do anything with it, as my drive is fairly unstable, and this would probably make it worse. I don't know.

---

### Post by caljohnsmith on 2009-01-27
sdc2 is only 1/2 GB, so if you wanted to keep it to avoid doing any changes to your system files, there's nothing wrong with that. sdc3 is actually the extended partition or "container" of your logical partitions. So do you want to make any partition changes, or are you OK with the way things are on your sdc drive? Like I mentioned, I can't think of any advantage of converting your sdc5 partition into a primary partition, but it's up to you.

---

### Post by djbushido on 2009-01-27
I don't really want to do anything, I'm just cloning drive at this point (thanks for other help) but just wanted to know if this was possible.

---

