---
title: "My USB pen drive mounts on read only!"
date: 2009-03-20
forum: General Help
---

### Post by Fixman on 2009-03-20
I can't really explain why, but every time I connect my USB pen drive to my computer it tells me its a "read only file system" and doesn't let me write on it!

The Pen Drive isn't nominated on /etc/fstab, and the USB part of my dmesg looks like this:

```

[269984.048049] usb 3-6: new high speed USB device using ehci_hcd and address 5
[269984.191297] usb 3-6: configuration #1 chosen from 1 choice
[269984.191932] scsi6 : SCSI emulation for USB Mass Storage devices
[269984.200549] usb-storage: device found at 5
[269984.200558] usb-storage: waiting for device to settle before scanning
[269989.200494] usb-storage: device scan complete
[269989.201749] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[269989.998454] sd 6:0:0:0: [sdc] 15671296 512-byte hardware sectors (8024 MB)
[269989.998969] sd 6:0:0:0: [sdc] Write Protect is off
[269989.998977] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[269989.998982] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[269990.000844] sd 6:0:0:0: [sdc] 15671296 512-byte hardware sectors (8024 MB)
[269990.001469] sd 6:0:0:0: [sdc] Write Protect is off
[269990.001477] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[269990.001482] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[269990.001494]  sdc: sdc1
[269990.002345] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[269990.002525] sd 6:0:0:0: Attached scsi generic sg2 type 0

```

Any help here?


EDIT: Without disconnecting of reconnecting my pen drive, I dmesg'ed again and this is the result:
```
 [270014.580965] FAT: Filesystem panic (dev sdc1)
[270014.580990]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.580996]     File system has been set read-only
[270014.582891] FAT: Filesystem panic (dev sdc1)
[270014.582898]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582903] FAT: Filesystem panic (dev sdc1)
[270014.582905]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582909] FAT: Filesystem panic (dev sdc1)
[270014.582911]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582915] FAT: Filesystem panic (dev sdc1)
[270014.582917]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582921] FAT: Filesystem panic (dev sdc1)
[270014.582923]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582927] FAT: Filesystem panic (dev sdc1)
[270014.582928]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582932] FAT: Filesystem panic (dev sdc1)
[270014.582934]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582938] FAT: Filesystem panic (dev sdc1)
[270014.582940]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582951] FAT: Filesystem panic (dev sdc1)
[270014.582953]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582957] FAT: Filesystem panic (dev sdc1)
[270014.582959]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582963] FAT: Filesystem panic (dev sdc1)
[270014.582965]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582969] FAT: Filesystem panic (dev sdc1)
[270014.582971]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582974] FAT: Filesystem panic (dev sdc1)
[270014.582976]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582980] FAT: Filesystem panic (dev sdc1)
[270014.582982]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582986] FAT: Filesystem panic (dev sdc1)
[270014.582988]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582992] FAT: Filesystem panic (dev sdc1)
[270014.582993]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.582997] FAT: Filesystem panic (dev sdc1)
[270014.582999]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.583004] FAT: Filesystem panic (dev sdc1)
[270014.583006]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.583014] FAT: Filesystem panic (dev sdc1)
[270014.583016]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.583020] FAT: Filesystem panic (dev sdc1)
[270014.583022]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.583026] FAT: Filesystem panic (dev sdc1)
[270014.583028]     fat_get_cluster: invalid cluster chain (i_pos 489162)
[270014.583032] FAT: Filesystem panic (dev sdc1)
[270014.583034]     fat_get_cluster: invalid cluster chain (i_pos 489162)

```

Now I'm scared.

---

### Post by Fixman on 2009-03-21
bump

---

