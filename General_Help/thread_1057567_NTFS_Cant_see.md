---
title: "NTFS Cant see"
date: 2009-02-01
forum: General Help
---

### Post by borisagrees on 2009-02-01
I cant see the partition that i took space from to install ubuntu, It is only used for storage and is a main partition, When ubuntu starts it Said failed to mount NTFS partition, Please use a microsoft compatable FSTAB editor, Here is some details (Note a USB Was plugged in at the time hence FAT16

From FSTAB

```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbec5a7fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40960000    7  HPFS/NTFS
/dev/sda2            5101       13302    65882565    7  HPFS/NTFS
/dev/sda3           13303       14594    10370048    7  HPFS/NTFS

Disk /dev/sdb: 500 MB, 500563968 bytes
16 heads, 32 sectors/track, 1909 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x2912d183

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1910      488816    6  FAT16
samuel@samuel-laptop:~$ 

```

I want to be able to use this drive as it has all my music, when it is mounted i will be windows free, it is only used for storage :popcorn:

---

### Post by Victormd on 2009-02-01
Was it "safely removed" the last time you used windows? If not, you will need to connect it via Windows then use the "safely remove" otherwise it will be locked for Ubuntu.
You can also run the following command from the terminal:
```
sudo fdisk -l
```
(that's a small L, not 1)
This will show all the partitions/HDs connected.

---

### Post by borisagrees on 2009-02-01
> **Victormd said:**
> Was it "safely removed" the last time you used windows? If not, you will need to connect it via Windows then use the "safely remove" otherwise it will be locked for Ubuntu.
You can also run the following command from the terminal:
```
sudo fdisk -l
```
(that's a small L, not 1)
This will show all the partitions/HDs connected.

No it was not removed.

It is SDA2 ( i think) In the fdisk above from terminal. But it will not show in the GUI and it wont let me mount SDA2 . it does not come with any error messages just wont show

---

### Post by brandon88tube on 2009-02-02
> **Victormd said:**
> Was it "safely removed" the last time you used windows? If not, you will need to connect it via Windows then use the "safely remove" otherwise it will be locked for Ubuntu.
You can also run the following command from the terminal:
```
sudo fdisk -l
```
(that's a small L, not 1)
This will show all the partitions/HDs connected.

Thats not true, if you do not safely remove a drive in Windows you can still mount it in Linux even if it gives you errors. You just have to force mount the drive.

---

### Post by Victormd on 2009-02-03
> **brandon88tube said:**
> Thats not true, if you do not safely remove a drive in Windows you can still mount it in Linux even if it gives you errors. You just have to force mount the drive.

Yes, you can force mount it, I didn't say that you couldn't. I just wanted the OP to run the command to check whether it was being recognized by fdisk or not, and if it was recognized, then one possibility for not mounting could be related to windows...

Since fdisk is recognizing the partition, then the OP should take a look at my signature to insert the proper string into fstab so the NTFS partition will auto-mount.

---

