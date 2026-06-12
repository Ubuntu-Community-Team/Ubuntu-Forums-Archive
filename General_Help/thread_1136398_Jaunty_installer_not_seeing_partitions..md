---
title: "Jaunty installer not seeing partitions."
date: 2009-04-25
forum: General Help
---

### Post by alexhatesmil on 2009-04-25
While trying to perform a clean install, the Jaunty partitioner fails to see the existing partitions of both of my hard drives. The partitions are all mountable and accessible within the file system, with the exception of my Windows XP system partition.

I currently have openSUSE installed, but will be replacing it with Jaunty. The openSUSE partitioner recognized all partitions.

Here is my fdisk -lu readout: 

> Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b7990

   Device      Boot             Start                           End                 Blocks   Id    System
/dev/sda1         *               63          19535039           9767488+   83    Linux
/dev/sda2             19535040          25398764             2931862+  82    Linux swap / Solaris
/dev/sda3                    25398765        220717034          97659135    83    Linux
/dev/sda4                 220717035        1465160129        622221547+     f     W95 Ext'd (LBA)
/dev/sda5                 220717098       1142125109      460704006        7    HPFS/NTFS
/dev/sda6         1142116352       1260363509           59123579        7    HPFS/NTFS
/dev/sda7              1260363776       1465157631        102396928       6    FAT16

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20fd20fc

   Device    Boot              Start                        End                 Blocks     Id    System
/dev/sdb1       *                      63         71682029         35840983+    7     HPFS/NTFS
/dev/sdb2                71682030        686087954       307202962+    f     W95 Ext'd (LBA)
/dev/sdb3            686087955      788502329          51207187+    7    HPFS/NTFS
/dev/sdb4             788494336      976784129       94144897    7    HPFS/NTFS
/dev/sdb5                71682093        481275269      204796588+     7    HPFS/NTFS
/dev/sdb6            481275333        686087954        102406311       7    HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12345678and my sfdisk -d readout:

> # partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 19534977, Id=83, bootable
/dev/sda2 : start= 19535040, size=  5863725, Id=82
/dev/sda3 : start= 25398765, size=195318270, Id=83
/dev/sda4 : start=220717035, size=1244443095, Id= f
/dev/sda5 : start=220717098, size=921408012, Id= 7
/dev/sda6 : start=1142116352, size=118247158, Id= 7
/dev/sda7 : start=1260363776, size=204793856, Id= 6
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size= 71681967, Id= 7, bootable
/dev/sdb2 : start= 71682030, size=614405925, Id= f
/dev/sdb3 : start=686087955, size=102414375, Id= 7
/dev/sdb4 : start=788494336, size=188289794, Id= 7
/dev/sdb5 : start= 71682093, size=409593177, Id= 7
/dev/sdb6 : start=481275333, size=204812622, Id= 7Any help would be appreciated.

---

### Post by adult swim on 2009-04-25
have you made sure that the disk you are trying to install on is unmounted?

---

### Post by alexhatesmil on 2009-04-25
As far as I can tell, both disks are unmounted.

---

