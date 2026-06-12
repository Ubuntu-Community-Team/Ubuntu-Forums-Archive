---
title: "mounting ext3 - yes weird"
date: 2005-09-24
forum: Desktop Environments
---

### Post by Jad on 2005-09-24
guys, I have little weird problem ,  I have (dev/hda7) partition and /dev/hdb1/ another hdd, both are ext3 but both not mounted

```

jad@madi:/$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        4865    39078081    f  W95 Ext'd (LBA)
/dev/hda5            4804        4865      497983+  82  Linux swap / Solaris
/dev/hda6               1        2492    20016895+  83  Linux
/dev/hda7            2493        4803    18563076   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2389    19189611   83  Linux
/dev/hdb2            2390        2482      747022+   5  Extended
/dev/hdb5            2390        2482      746991   82  Linux swap / Solaris
```

```

jad@madi:/$ df -T -h
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda6     ext3     19G  1.6G   17G   9% /
tmpfs        tmpfs    126M     0  126M   0% /dev/shm
/dev/hda7     ext3     18G  101M   17G   1% /home
/dev       unknown     19G  1.6G   17G   9% /.dev
none         tmpfs    5.0M  2.8M  2.3M  56% /dev

```



```

jad@madi:/$ mount
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda7 on /home type ext3 (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

```


please advise.

---

### Post by Hairy_Palms on 2005-09-24
what happens if you try to mount them manually with
sudo mount -t ext3 /dev/hda7 /home/folder any error output?

---

### Post by Jad on 2005-09-25
.

---

