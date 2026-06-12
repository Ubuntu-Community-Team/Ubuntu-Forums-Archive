---
title: "tried to backup my files and lost everything except /dev/zero!"
date: 2009-01-08
forum: General Help
---

### Post by zachbb on 2009-01-08
I needed to backup my computer files (including on my mounted windows partition) to my external harddrive, so I click and dragged everything in the root to my external harddrive using nautilus.

I checked the used space on my external hd and it was the same as on my filesystem, so I figured everything would be ok.

Now I have reformatted my harddrive, but the backup seems to be missing loads of files. The backup only has three directories:

/bin
/boot
/dev

and there is one HUGE (132GB) file called /dev/zero

I am assuming all my data is in that file.... how can I recover it?

---

### Post by hyper_ch on 2009-01-08
what's the output of
```

sudo fdisk -l

```
and
```

df

```

---

### Post by bryncoles on 2009-01-08
stop using the drive, boot a live cd or something to reduce the risk of writing anything to the drive (that'll permanently destroy data) and have yourself a pre-emptive look at 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

they're free, open source data recovery tools which are available in the repo's. the websites there provide good walkthroughs on how to use them.

---

### Post by zachbb on 2009-01-08
here is output from ls -l:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14333       14594     2096128   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       12675    91268096    7  HPFS/NTFS
/dev/sda4           12676       14332    13309852+   5  Extended
/dev/sda5           12676       14256    12699351   83  Linux
/dev/sda6           14257       14332      610438+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.0 GB, 16039018496 bytes
75 heads, 40 sectors/track, 10442 cylinders
Units = cylinders of 3000 * 512 = 1536000 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10443    15663084    c  W95 FAT32 (LBA)

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS




here is output from df:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             12499836   4005648   7859224  34% /
tmpfs                  1035860         0   1035860   0% /lib/init/rw
varrun                 1035860       212   1035648   1% /var/run
varlock                1035860         0   1035860   0% /var/lock
udev                   1035860      2840   1033020   1% /dev
tmpfs                  1035860       236   1035624   1% /dev/shm
lrm                    1035860      2000   1033860   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda3             91268092  11935632  79332460  14% /media/OS
/dev/sdb1             15647784   7086856   8560928  46% /media/Lexar
/dev/sdc1            976760000 139168200 837591800  15% /media/disk


---

### Post by zachbb on 2009-01-08
> **bryncoles said:**
> stop using the drive, boot a live cd or something to reduce the risk of writing anything to the drive (that'll permanently destroy data) and have yourself a pre-emptive look at 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

they're free, open source data recovery tools which are available in the repo's. the websites there provide good walkthroughs on how to use them.

should I install and run these programs from the live cd? or should I install them on the linux partition of my computer (it's the same computer on which my data has gone, but I only need to recover my data from my windows partition)?

---

### Post by bryncoles on 2009-01-08
well, first you'll need a separate hard drive to write data to. obviously you cant put the files you're recovering on the drive you're recovering them from, as they'll just get saved over other, yet-to-be-recovered files. 

are your windows partitions separate from the ubuntu one? and the same size? if so, two choices (as i see it), which are run from the live cd which will be slower but safer, or if your windows drives are separate then you might as well install and run them from there. that'd be quicker. 

the only real advice id give is read everything on the websites i linked, so you understand what the procedure involves and how to do it correctly. 

then... best of luck!

---

