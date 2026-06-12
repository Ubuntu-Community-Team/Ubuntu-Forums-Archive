---
title: "mounting permissions?"
date: 2009-02-25
forum: General Help
---

### Post by antonyant11 on 2009-02-25
the problem is I cant access my ntfs drives through dolphin. I click on them but the selected item just reverts to root or home. tells me only root can mount the drives.
 
 i was wondering .. mabe a permission problem..?

ant@conan-the-destroyer:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf28af28a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       38912   281844360    f  W95 Ext'd (LBA)
/dev/sda5            7650       38912   251120016    7  HPFS/NTFS
/dev/sda6            3825        7486    29414952   83  Linux
/dev/sda7            7487        7649     1309266   82  Linux swap / Solaris

Partition table entries are not in disk order

thanks

---

### Post by ajmorris on 2009-02-26
hi there,
strange... it should be using ntfs-3g by default, if you are using an up-to-date version of ubuntu. It will most likely be one of 2 things. Either it is not using ntfs-3g and your ntfs kernel module configuration does not allow mounting from a normal user, or your ntfs partition has a dirty flag set, so it is not mounting. 
(I am assuming your ntfs partition is a windows install) First of all, try rebooting your machine and logging in to windows, then rebooting correctly, to remove the dirty flag.
If you can still not mount them in dolphin, try mounting them manually in a terminal:

```
sudo mount -t ntfs-3g /dev/sda5 /mnt/windows
```

NOTE: you can try mounting the partition without sudo to mount it without super user priveledges. Also, replace /mnt/windows with where ever you would like the windows partition to be mounted to (the destination **must** already exist)

if this does not work, you can try to 'force' the partition to mount:

```
sudo mount -t ntfs-3g -o force /dev/sda5 /mnt/windows
```

AJ

---

