---
title: "automatic mount problem of my USB Harddrive"
date: 2008-12-14
forum: Desktop Environments
---

### Post by mdzahidh on 2008-12-14
I have a transcend USB harddrive. But when i plug it in, gnome says it cannot mount the volume and following is the output of dmesg

 usb 7-1: USB disconnect, address 2
[ 1382.826439] usb 7-1: new high speed USB device using ehci_hcd and address 4
[ 1382.959278] usb 7-1: configuration #1 chosen from 1 choice
[ 1382.959838] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1382.959985] usb-storage: device found at 4
[ 1382.959987] usb-storage: waiting for device to settle before scanning
[ 1386.866188] usb-storage: device scan complete
[ 1386.866854] scsi 7:0:0:0: Direct-Access     StoreJet Transcend             PQ: 0 ANSI: 2 CCS
[ 1386.874464] sd 7:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 1386.875455] sd 7:0:0:0: [sdb] Write Protect is off
[ 1386.875462] sd 7:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 1386.875467] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1386.877024] sd 7:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 1386.877708] sd 7:0:0:0: [sdb] Write Protect is off
[ 1386.877714] sd 7:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 1386.877719] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1386.877726]  sdb: sdb1
[ 1387.352501] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 1387.352590] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 1387.735340] UDF-fs: No partition found (1)
[ 1387.780516] ISOFS: Unable to identify CD-ROM format.
[ 4949.649848] UDF-fs: No partition found (1)
[ 4949.696232] ISOFS: Unable to identify CD-ROM format.

As it can be seen that for some reason the system confuses it with CD-Rom !!.. How do i fix this ?

---

### Post by taurus on 2008-12-14
What filesystem is that harddrive?  Can you post the output of this command from a terminal (with the drive plugged in)?

```
sudo fdisk -l
```

---

### Post by mdzahidh on 2008-12-16
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13        1318    10485760    7  HPFS/NTFS
/dev/sda3   *        1318       28079   214958080    7  HPFS/NTFS
/dev/sda4           28080       38914    87025258    f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           28080       28577     4000153+  82  Linux swap / Solaris
/dev/sda7           28578       38586    80397261   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd688765

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS




the /dev/sdb1 is the USB HDD in question.

---

### Post by taurus on 2008-12-16
Try something like

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```
And if you get a message about not safely remove your hardware the last time you use it, then just add the force option at the end to mount it.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```
Make sure to unmount it first, Safely Remove Hardware, before you unplug it when you use it in windows.

---

### Post by mdzahidh on 2008-12-20
i know how to mount things using "mount" 

What i wanted to know is why is Gnome thinking my USB Hardrive is a CD-ROM and failing to mount automatically ? Also how do i change how gnome mounts stuffs. The gconf-editor didn't come too useful to solve this :S

---

### Post by taurus on 2008-12-20
What does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by mdzahidh on 2008-12-21
> **taurus said:**
> What does your /etc/fstab look like?

```
cat /etc/fstab
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=3ee84be2-1981-48de-a8d0-1a63e0e0bdb2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=db58711e-0fc5-4b78-a3ff-697d4dd9f62f none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
localhost:/wuala /root/wuala/direct nfs defaults,users,noauto,rsize=8192,wsize=8192,timeo=14,intr,nolock,soft

---

### Post by mdzahidh on 2008-12-21
hey, as soon as i pasted my fstab here, i noticed that /dev/sdb1 has been entered as udf format...but who added this entry in the fstab, at least i didn't !!!

---

