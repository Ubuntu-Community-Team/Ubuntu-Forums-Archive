---
title: "Recover corrupted NTFS with Ubuntu."
date: 2010-02-08
forum: Desktop Environments
---

### Post by hariks0 on 2010-02-08
I have a 250 GB external HD in NTFS. It was used to transport data between my office [Windoze] and home [Ubuntu 9.10]. While doing a reinstall of wxp this HD was attached to the office pc. Now the File system of this External HD is Raw. I am sure that wxp has not formatted this as the result would be only an NTFS disk, not raw. I tried the disk utility in Ubuntu and the it displays that the Disk is healthy.

Is there a way to get the data in this disk back using Ubuntu utilities. I thought I would wait for your replies before formatting.:(

---

### Post by Zorael on 2010-02-08
It depends on what happened, I guess. It sounds like the partition table was deleted.

You can try using **testdisk** (in the universe repositories) to search for lost partitions. That should work if the partition is still physically *there* but undefined in the (potentially missing) table.

---

### Post by jenaniston on 2010-02-08
> **hariks0 said:**
> I have a 250 GB external HD in NTFS. . . . While doing a reinstall of wxp **this HD was attached to the office pc**. 
Now the File system of this External HD is Raw. I am sure that wxp has not formatted this as the result would be only an NTFS disk, not raw. I tried the disk utility in Ubuntu and the it displays that the Disk is healthy.

Is there a way to get the data in this disk back using Ubuntu utilities. I thought I would wait for your replies before formatting.:(

I have used linux - Fedora or Ubuntu - to rescue files off partitions messed up by Windows . . .
and would be encouraging that it ***may be ***very probable for you to get at these files . . .

How do the different partition utilities "see" the external HD . . . ?
do not assume all will see it the same when it is corrupted/messed up.

Try
```
# sfdisk -l
```also see and compare results from . . .
**parted ** 
then at prompt **parted > select /dev/hdx** (select device)  ( usually have to q quit)
**cfdisk**  **/dev/hdx**  (need to specify device. . . and then quit at table "button")

Don't write anything to (reformat)  the partition - just list the partition and filesystem type.

---

### Post by hariks0 on 2010-02-15
Now here are the outputs:-

```
hari@Indira:~$ sudo sfdisk -l

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   6373    6374-  51199123+  83  Linux
/dev/sda2       6374   30400   24027  192996877+   f  W95 Ext'd (LBA)
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       6374+  12747    6374-  51199123+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda6      12748+  19121    6374-  51199123+   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda7      29793+  30400     608-   4883728+  82  Linux swap / Solaris
/dev/sda8      19122+  21889    2768-  22233928+  83  Linux
/dev/sda9      21890+  29792    7903-  63480816   83  Linux

Disk /dev/sdb: 5690 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  30399   30400- 244187968+   7  HPFS/NTFS
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

```

Both 'parted' and 'cfdisk' returned error messages. But Gparted recognizes the 250 GB HD as unallocated 43.59 GB.

Also my pc refused to boot with this HD connected via USB. It was not so before. So it seems that after running 'Testdisk' there had been some improvement.

---

