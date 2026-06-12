---
title: "Grub Error 22"
date: 2009-04-23
forum: General Help
---

### Post by ukblacknight on 2009-04-23
Just done a fresh install to Ubuntu 9.04!  It's not all plain sailing however, as I'm getting the Grub 22 error on boot, after Stage 1.5.  I remember having problems on my last upgrade and getting Vista working.

I posted something in the forums in November regarding problems booting Vista, in which the setup would boot Ubuntu.  Below was my 8.10 setup in November that **worked**.

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x082a3b4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   320608255   160303104    7  HPFS/NTFS
/dev/sda2       320609205   322601264      996030   82  Linux swap / Solaris
/dev/sda3       322601265   342730709    10064722+  83  Linux
/dev/sda4   *   342730710   488392064    72830677+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f114b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c3ebc67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   241248104   120624021    7  HPFS/NTFS

Disk /dev/sdd: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794175 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              44    15679439     7839698    b  W95 FAT32

```

Note how sda4 is the boot device.  Below is my current setup after the install:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x082a3b4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   320608255   160303104    7  HPFS/NTFS
/dev/sda2       320609205   322601264      996030   82  Linux swap / Solaris
/dev/sda3       322601265   488392064    82895400    5  Extended
/dev/sda5       322601328   382604039    30001356   83  Linux
/dev/sda6       382604103   488392064    52893981   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f114b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c3ebc67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   241248104   120624021    7  HPFS/NTFS

Disk /dev/sde: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794175 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              44    15679439     7839698    b  W95 FAT32

```

The boot seems to be on the NTFS (Windows Vista) partition.  Now I've got a bit of a strange setup here, largely due to the motherboard seeing PATA drives taking priority over SATA.

I've tried doing a fix, however it didn't work.

```

find /boot/grub/stage1
 (hd0,5)

```

I ran the root (hd0,5) and setup (hd0) but that didn't do anything.  I think that grub should be on sdc1.

If anyone could point me in the right direction on getting the boot setup correctly, it'd be much appreciated :)

---

