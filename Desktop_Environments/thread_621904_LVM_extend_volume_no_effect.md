---
title: "LVM extend volume: no effect?"
date: 2007-11-24
forum: Desktop Environments
---

### Post by Spiri82 on 2007-11-24
Hey all,

I have a problem with Logical Volume Manager. I extended a volume with another harddisk, but the free space of the volume doesn't seem to increase.

Gnome gives me the following information about the volume:

Volume: Video
Contents: 2593 items, totalling 574.7 GB
Free space: 166.0 MB

In a terminal, I get the information below though. Does any of you have an idea what I forgot?

Kevin


kevin@Ziggy:~$ sudo vgdisplay
[sudo] password for kevin:
  --- Volume group ---
  VG Name               video
  System ID             
  Format                lvm2
  Metadata Areas        4
  Metadata Sequence No  5
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                4
  Act PV                4
  VG Size               674.30 GB
  PE Size               4.00 MB
  Total PE              172622
  Alloc PE / Size       172455 / 673.65 GB
  Free  PE / Size       167 / 668.00 MB
  VG UUID               AaHI3g-S3QK-1o9P-TEuN-xaeC-FOMk-WMA0Ee
   
kevin@Ziggy:~$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdb2
  VG Name               video
  PV Size               200.43 GB / not usable 506.00 KB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              51311
  Free PE               0
  Allocated PE          51311
  PV UUID               xlXLDq-xpWy-dw0z-Srv8-x7xo-1qLD-F2FJ1d
   
  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               video
  PV Size               189.92 GB / not usable 2.32 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              48618
  Free PE               0
  Allocated PE          48618
  PV UUID               eUQH1f-GFJL-Np6L-ZwGV-UxH5-rTxV-BltE4F
   
  --- Physical volume ---
  PV Name               /dev/sda1
  VG Name               video
  PV Size               186.31 GB / not usable 3.69 MB
  Allocatable           yes 
  PE Size (KByte)       4096
  Total PE              47694
  Free PE               167
  Allocated PE          47527
  PV UUID               TyCCoc-wwA2-J1ty-JKMe-XJC1-PAaw-tNVmr1
   
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               video
  PV Size               97.65 GB / not usable 2.32 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              24999
  Free PE               0
  Allocated PE          24999
  PV UUID               GpUdI8-AHeS-OZDe-8y2v-Y0af-jXiI-CujZtV
   
kevin@Ziggy:~$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/video/Video
  VG Name                video
  LV UUID                DCQeMx-k0ap-BpZT-12tc-9GKK-J9C9-yy1yBJ
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                673.65 GB
  Current LE             172455
  Segments               4
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0
   
kevin@Ziggy:~$

---

### Post by Spiri82 on 2007-12-14
Found the answer myself, and figured out I'm posting at the wrong board, maybe the admins can move this thread? Sorry for the trouble.

The answer was that I needed to use the xfs_growfs command to adjust the file system.

---

