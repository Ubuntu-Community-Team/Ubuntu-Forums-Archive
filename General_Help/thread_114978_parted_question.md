---
title: "parted question"
date: 2006-01-09
forum: General Help
---

### Post by matthinckley on 2006-01-09
OK i've used gparted and parted before.. but ever since I installed windows on my machine in a new partition when I try to do anything in parted this is what I get:

```
Error: Unable to satisfy all constraints on the partition.
```

what does this mean and can I fix this without completely repartitioning and reinstalling?

This is what I get from fdisk -l
```

omitting empty partition (5)

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3556    28563538+  83  Linux
/dev/hda2   *        3557        7112    28563570    c  W95 FAT32 (LBA)
/dev/hda3            7113       19457    99161212+   5  Extended
/dev/hda4           19270       19457     1510078+  82  Linux swap / Solaris
/dev/hda5            7113       19269    97651039+  83  Linux
```

also strangely enough (to me anyways.. this probably makes perfect sense to everyone else).. my swap partition was originally hda5 and I have a Storage partition that was originally hda6, but after i installed windows these changed to hda4 and hda5 respectively..

Thanks

Matt

---

### Post by dcstar on 2006-01-09
[QUOTE=matthinckley].......
This is what I get from fdisk -l
```

**omitting empty partition (5)**

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3556    28563538+  83  Linux
/dev/hda2   *        3557        7112    28563570    c  W95 FAT32 (LBA)
/dev/hda3            7113       19457    99161212+   5  Extended
/dev/hda4           19270       19457     1510078+  82  Linux swap / Solaris
/dev/hda5            7113       19269    97651039+  83  Linux
```

also strangely enough (to me anyways.. this probably makes perfect sense to everyone else).. my swap partition was originally hda5 and I have a Storage partition that was originally hda6, but after i installed windows these changed to hda4 and hda5 respectively..

Thanks

Matt[/QUOTE]
The top line says that gparted has ignored a partition it thinks is empty, the Windows partition process has done something which has confused gparted.

If you run the Windows fdisk utility, it will probably show something different.

Try the "cfdisk" utility and see what comes up (be careful!).

---

### Post by matthinckley on 2006-01-09
ok this is what I get from cfdisk
```

                                  cfdisk 2.12p

                              Disk Drive: /dev/hda
                       Size: 160041885696 bytes, 160.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 19457

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1                    Primary   Linux ext3       [/]             29249.10
    hda2        Boot        Primary   W95 FAT32 (LBA)                  29249.10
                            Logical   Free Space                           0.01*
    hda5        NC          Logical   Linux ext3   [/mnt/storage]     99994.73*                                  
                            Logical   Free Space                           0.04*
    hda4                    Primary   Linux swap / Solaris              1546.33*





     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition

```

---

### Post by dcstar on 2006-01-09
[QUOTE=matthinckley]ok this is what I get from cfdisk
......[/QUOTE]
Notice how there are 6 entries, while the fdisk only listed 5?

Don't worry about it, Windows has changed the start/end boundaries of some of its partitions and left a little (unusable) disk space in-between partitions, and this has confused the Linux fdisk utility.

---

### Post by matthinckley on 2006-01-09
yeah everything works fine, i just didn't know if there was some way to fix it so parted could read it again

---

### Post by dcstar on 2006-01-09
[QUOTE=matthinckley]yeah everything works fine, i just didn't know if there was some way to fix it so parted could read it again[/QUOTE]
You could try and delete the small partitions, but be careful!

---

### Post by matthinckley on 2006-01-09
can't delete them.. they're just free space

---

