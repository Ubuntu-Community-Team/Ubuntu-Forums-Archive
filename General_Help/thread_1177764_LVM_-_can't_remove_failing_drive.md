---
title: "LVM - can't remove failing drive"
date: 2009-06-03
forum: General Help
---

### Post by sylaan on 2009-06-03
Hi all, 

I use LVM over 3 physical volumes: 

```
root@neriak:~# pvscan
  PV /dev/sdb1   VG storage   lvm2 [186.30 GB / 0    free]
  PV /dev/sda4   VG storage   lvm2 [200.87 GB / 0    free]
  PV /dev/sdc1   VG storage   lvm2 [149.05 GB / 16.00 MB free]
  Total: 3 [536.22 GB] / in use: 3 [536.22 GB] / in no VG: 0 [0   ]
```

The sda drive is failing and I want to remove /dev/sda4 from the group, without much success though. If I look at the disk space I see the following: 

```
root@neriak:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G  6.3G   13G  34% /
tmpfs                 245M     0  245M   0% /lib/init/rw
varrun                245M  592K  244M   1% /var/run
varlock               245M     0  245M   0% /var/lock
udev                  245M  148K  245M   1% /dev
tmpfs                 245M  1.1M  244M   1% /dev/shm
lrm                   245M  2.7M  242M   2% /lib/modules/2.6.28-12-generic/volatile
/dev/sda3             9.9G  3.3G  6.1G  35% /home
/dev/mapper/storage-storage1
                      528G   38G  474G   8% /storage
//nas/storage         915G  701G  214G  77% /nas
```

As you can see, /dev/mapper/storage-storage1 shows 474GB free and yet when I do a pvdisplay: 

```
root@neriak:~# vgdisplay
  --- Volume group ---
  VG Name               storage
  System ID             
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               536.22 GB
  PE Size               4.00 MB
  Total PE              137272
  Alloc PE / Size       137268 / 536.20 GB
  Free  PE / Size       4 / 16.00 MB
  VG UUID               SS2wO5-K12B-wSo1-iceX-VSiT-aYPQ-zdgEuU
```

All PEs are allocated which means pvmove fails, can't move data off /dev/sda4: 

```
root@neriak:~# pvmove /dev/sda4
  Insufficient free space: 51422 extents needed, but only 4 available
  Unable to allocate mirror extents for pvmove0.
  Failed to convert pvmove LV to mirrored

```

What am I doing wrong ? How can I move data off the failing drive ? there should be plenty of space on the other PEs. Any help is appreciated. 

Thanks,
Sylaan

---

### Post by sylaan on 2009-06-06
Anyone ?

---

