---
title: "fdisk novice needs help"
date: 2009-03-07
forum: General Help
---

### Post by TristanSt on 2009-03-07
My Dell laptop has the habit of molesting my MBR whenever I accidently press the "Media Direct" button. Originally this didn't do much harm, but this time it's broken things.

Typically, I hadn't backed up the MBR with DD - I will now.

Anyway, here's how the config used to be (printed using fdisk -l):
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  de  Dell Utility
/dev/sda2              17        1322    10485760    7  HPFS/NTFS
/dev/sda3   *        1323       11064   201676758    7  HPFS/NTFS
/dev/sda4           11065       38914   100270850+   f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           26431       38087    93634821   83  Linux
/dev/sda7           38088       38586     4008186   82  Linux swap / Solaris
/dev/sda8           11065       18713    61440529+   7  HPFS/NTFS

```

And here's how it looks now:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       38587       38914     2620416    c  W95 FAT32 (LBA)
/dev/sda2              17        1322    10485760    7  HPFS/NTFS
/dev/sda3   *        1323       11064    78252615    7  HPFS/NTFS
/dev/sda4           11065       38914   223698276    f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           26431       38087    93634821   83  Linux
/dev/sda7           38088       38586     4008186   82  Linux swap / Solaris
/dev/sda8           11065       18713    61440529+   7  HPFS/NTFS

Partition table entries are not in disk order

```


Things that I know and don't care about:
1. There is a big gap between sda3 and sda6.
2. Partition table entries aren't in order.

The issue that I'm trying to resolve is that sda1 has been replaced by an entry that is the same as sda5. I'd like my sda1 to be put back and sda5 to be left alone. Note, I don't want to move any data around at all.

The other thing worth noting is that cfdisk and parted wont work because sda1 and sda5 are overlapping. 

Any ideas?

---

### Post by murataht on 2009-03-07
I am not much of a fdisk expert. but, I think it is better to backup your things before any further operation.

if you are ready to "repair" your mbr, maybe you should try testdisk utility. you can install it from apt directly.

```
 apt-get install testdisk 
```

and consult the man page to how to use.

good luck.

---

