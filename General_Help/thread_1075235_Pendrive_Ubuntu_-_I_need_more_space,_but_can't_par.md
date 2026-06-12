---
title: "Pendrive Ubuntu - I need more space, but can't partition the drive"
date: 2009-02-20
forum: General Help
---

### Post by kyleflan on 2009-02-20
I installed Ubuntu on my 8GB USB drive via Administration -> Create a USB Startup Disk and selected to use half of the drive for Ubuntu and leave the other half for normal storage. Well, it turns out I want more space than I planned in the beginning. 

I opened up GParted thinking I could possibly extend the partition Ubuntu was on, but GParted only showed one big partition on the disk. (See attached screenshot)

Here's the output of fdisk p

```
Disk /dev/sdb: 8029 MB, 8029470208 bytes
50 heads, 32 sectors/track, 9801 cylinders
Units = cylinders of 1600 * 512 = 819200 bytes
Disk identifier: 0x0001003b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9802     7841279    c  W95 FAT32 (LBA)

```

Does anyone know how I could extend the Ubuntu partition without having to reinstall?

Thanks,
Kyle

---

### Post by caljohnsmith on 2009-02-20
Would you please also post the output of:
```
sudo fdisk -lu
```
Also, it looks like your Ubuntu partition clearly takes up the entire 8 GB drive now, so you can't make it any bigger.

---

### Post by dcstar on 2009-02-20
> **kyleflan said:**
> I installed Ubuntu on my 8GB USB drive via Administration -> Create a USB Startup Disk and selected to use half of the drive for Ubuntu and leave the other half for normal storage. Well, it turns out I want more space than I planned in the beginning. 

I opened up GParted thinking I could possibly extend the partition Ubuntu was on, but GParted only showed one big partition on the disk. (See attached screenshot)
..........
Does anyone know how I could extend the Ubuntu partition without having to reinstall?


AFAIK there should be two things inside that partition, the Ubuntu install and space set aside for a "casperw" partition/file.

Gparted shows only 50% of the partition used, so there should be space (somewhere) then you boot it.

---

### Post by kyleflan on 2009-02-20
> **caljohnsmith said:**
> Would you please also post the output of:
```
sudo fdisk -lu
```
Also, it looks like your Ubuntu partition clearly takes up the entire 8 GB drive now, so you can't make it any bigger.

```
sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 8029 MB, 8029470208 bytes
50 heads, 32 sectors/track, 9801 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001003b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1    15682558     7841279    c  W95 FAT32 (LBA)

```

---

