---
title: "Drive labels change after reboot"
date: 2008-10-19
forum: Desktop Environments
---

### Post by krow_drah on 2008-10-19
Hello I'm new to Ubuntu.
I'm trying to auto mount some drives on my box (Dell workstation 380).

1) 150 GB SATA drive plugged into mother board
2) 750 GB IDE drive plugged into ATA controller (side issue: drive is detected at SATA e.g., sdx, rather than hdx)
3) 1500 GB SATA II drive plugged into PROMISE SATA300 TX4 PCI SATA II Controller Card.

My problem, which I have not yet seen in the forums, is that the drive labels, reported by fdisk -l, change after reboot. So I cannot successfully auto mount them by adding their disk labels to /etc/fstab.
I'd like to keep the disk labels constant and I'm worried this has something to do with my SATA controller card. Why are the disk labels changing and how can I stop them from changing?

For example:
```
fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15a415a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17495   140528556   83  Linux
/dev/sda2           17496       18241     5992245    5  Extended
/dev/sda5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa319994e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdbf635f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       90940   730475518+  83  Linux
/dev/sdc2           90941       91427     3911827+  82  Linux swap / Solaris
/dev/sdc3           91428      182401   730748655   83  Linux
```

...then after a reboot...

```
fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdbf635f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       90940   730475518+  83  Linux
/dev/sda2           90941       91427     3911827+  82  Linux swap / Solaris
/dev/sda3           91428      182401   730748655   83  Linux

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15a415a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17495   140528556   83  Linux
/dev/sdb2           17496       18241     5992245    5  Extended
/dev/sdb5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa319994e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001    7  HPFS/NTFS
```


--------
any help appreciated!

---

### Post by krow_drah on 2008-10-19
Solution

rather than edit the fstab changing the labels, e.g., sda, specify and edit the UUID which is unique to the drive.

UUID info here:

[http://ubuntuforums.org/showthread.php?t=223182&highlight=uuid](http://ubuntuforums.org/showthread.php?t=223182&highlight=uuid)

---

