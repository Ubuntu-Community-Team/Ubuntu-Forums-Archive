---
title: "Fdisk Not Working"
date: 2008-12-08
forum: General Help
---

### Post by jcm4 on 2008-12-08
On my Dell XPS M1530, I'm trying to mount an external hard drive by following the steps shown here: [http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux](http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux)
On the first step, when I type in fdisk -1 I get returned with "fdisk: invalid option -- '1'".
How do I fix it?

---

### Post by Sicaine on 2008-12-08
Use a small L = l not a one

---

### Post by jcm4 on 2008-12-08
Alright, did that got this:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS
But nowhere does it say creating mount point. I continued with the steps and got no results. Help?

---

### Post by taurus on 2008-12-08
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sdb1 /media/windows
df -h
```

---

### Post by jcm4 on 2008-12-08
Got it, didn't even have to mount it, just had to go back to Windows and safely remove. Thanks.

---

