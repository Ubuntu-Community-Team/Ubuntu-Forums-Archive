---
title: "[SOLVED] Cannot Get USB Flash Drive to Automount"
date: 2009-01-01
forum: General Help
---

### Post by morning_napalm on 2009-01-01
I have a new 8GB Flash drive that does not mount when I insert it.  I have other flash drives that still seem to work fine.

Looking at  some similar topics I have run the following commands and posted the results.

dmesg | tail
> [25127.183324] sd 14:0:0:0: [sdd] Write Protect is off
[25127.183332] sd 14:0:0:0: [sdd] Mode Sense: 00 00 00 00
[25127.183336] sd 14:0:0:0: [sdd] Assuming drive cache: write through
[25127.186431] sd 14:0:0:0: [sdd] 15794176 512-byte hardware sectors (8087 MB)
[25127.187061] sd 14:0:0:0: [sdd] Write Protect is off
[25127.187067] sd 14:0:0:0: [sdd] Mode Sense: 00 00 00 00
[25127.187069] sd 14:0:0:0: [sdd] Assuming drive cache: write through
[25127.187075]  sdd: sdd1
[25127.382218] sd 14:0:0:0: [sdd] Attached SCSI removable disk
[25127.382313] sd 14:0:0:0: Attached scsi generic sg5 type 0


sudo fdisk -l
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9eef9eef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x877f9f73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+  83  Linux
/dev/sdb2            2551       30146   221664870   83  Linux
/dev/sdb3           30147       30401     2048287+  82  Linux swap / Solaris

Disk /dev/sdd: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         984     7897056+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 13)


I can mount the device using, but I'm not sure how to change permissions to write to it. 
```
sudo mount -t vfat /dev/sdd1 /media/flash
```

Can someone please help me fix this so that it automatically mounts when inserted.

Thank you.

---

### Post by morning_napalm on 2009-01-02
Well - my son placed a file on the USB drive from another computer and then tried again.  This time it mounted with no problems.

I am wondering if it had something to do with the different "physical/logical endings" and if this corrected itself when he added a file to the drive.

I would be curious if anyone has an answer, but we did get it working.

---

