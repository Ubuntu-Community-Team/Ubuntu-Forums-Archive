---
title: "[SOLVED] LVM vgcreate fails, pvcreate is inconsistant"
date: 2007-01-28
forum: Desktop Environments
---

### Post by DantePasquale on 2007-01-28
Hi, I'm following the LVM tutorial on howtoforge and I've run into some issues with pvcreate and lvcreate.  Here is the environment:

```
~$ uname -a
Linux inferno 2.6.15-27-amd64-generic #1 SMP PREEMPT Fri Dec 8 17:50:54 UTC 2006 x86_64 GNU/Linux
```

```
sudo fdisk -l /dev/sda

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2040    16386268+  83  Linux
/dev/sda2            2041        2805     6144862+  82  Linux swap / Solaris
/dev/sda3            2806       15553   102398310   83  Linux
/dev/sda4           15554       91201   607642560    5  Extended
/dev/sda5           15554       60172   358402086   8e  Linux LVM
/dev/sda6           60173       91201   249240411   8e  Linux LVM


sudo fdisk -l /dev/sdb
Password:

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38245   307202931   8e  Linux LVM
/dev/sdb2           38246       70115   255995775   8e  Linux LVM
/dev/sdb3           70116       91201   169373295   8e  Linux LVM
```

I then run pvcreate on tje 4 8e partitions ; pvdisplay shows ...
```

sudo pvdisplay | more
  --- NEW Physical volume ---
  PV Name               /dev/evms/sda5
  VG Name
  PV Size               341.80 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               NQ8cnG-kifh-xVNu-1XBa-X1mP-6CTp-05FhwX

  --- NEW Physical volume ---
  PV Name               /dev/evms/sda6
  VG Name
  PV Size               237.69 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               qhvn4w-s3yJ-Gomb-8ESZ-fZAt-1guU-P1yCKr

  --- NEW Physical volume ---
  PV Name               /dev/evms/sdb1
  VG Name
  PV Size               292.97 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               ZLUuTs-21J7-2cUC-OcY7-tJjd-YAAq-EBlpF8

  --- NEW Physical volume ---
  PV Name               /dev/evms/sdb2
  VG Name
  PV Size               244.14 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               ipotZw-7dKW-SmOG-XmVH-Vlal-hAbf-26fkCA
```

Looking good, so I want to create a volume group, web-files, from /dev/hda5 /dev/hdb1

```
sudo vgcreate -v web-pages /dev/hda5 /dev/hdb1
    Wiping cache of LVM-capable devices
    Adding physical volume '/dev/hda5' to volume group 'web-pages'
  /dev/hda5 not identified as an existing physical volume
  Unable to add physical volume '/dev/hda5' to volume group 'web-pages'.
```

I've tried various combinations of the 8e partitions and always get the same result on the first or only partition listed.

Any help on debugging is greatly appreciated!

Dante

---

### Post by DantePasquale on 2007-01-30
Hi All,

Here's what I found out.  When you run pvcreate /dev/sda5 it creates a new device in the dev tree.  I found it under /dev/evsm/sda5.  If I use those devices in vgcreate then vgcreate succeeds.  For example, vgcreate web-docs /dev/evsm/sda5 /dev/evsm/sdb1 then the volume group is indeed created!

Now the question is why is this happening on ubuntu 6.06 LTS?  Why is this o/s different from, say RH Enterprise 4.0?

Thanks,
Dante

---

### Post by talowe on 2007-01-30
> **DantePasquale said:**
> Hi All,



Now the question is why is this happening on ubuntu 6.06 LTS?  Why is this o/s different from, say RH Enterprise 4.0?

evms == Enterprise Volume Management System.  I had it installed before upgrading to 6.06, so didn't know it was installed by default w/6.06, but is a nice system for managing all of your storage, not just LVM's.  If it is not installed, try package 'evms-gui' for a graphical tool to manage your partitions (create,delete, shrink, grow, etc.).  ncurses and commandline tools are also available.  The terminology is slightly different, but not hard to pick up on.  There are tutorials and docs online.  Don't have any references handy, but google should produce many.

Tom

---

