---
title: "sbackup opens File Browser approx every 1/2hr"
date: 2011-03-30
forum: Desktop Environments
---

### Post by hedge.hog on 2011-03-30
Hi,
I've configured, and successfully run, sbackup.

The problem is that approx every 1/2hr the File Browser window pops up, open at the mounted backup drive (usb).
This occurs even if I unmount the drive in Nautilus.

Appreciate any insights, tips or hints at what might be going wrong.

In syslog I see this at the times when the broswer opens:

```
Mar 28 07:23:27 desktop kernel: [74859.246612] usb 1-8: USB disconnect, address 55
Mar 28 07:23:39 desktop kernel: [74871.240525] usb 1-8: new high speed USB device using ehci_hcd and address 56
Mar 28 07:23:39 desktop kernel: [74871.391841] usb 1-8: configuration #1 chosen from 1 choice
Mar 28 07:23:39 desktop kernel: [74871.392281] scsi35 : SCSI emulation for USB Mass Storage devices
Mar 28 07:23:39 desktop kernel: [74871.392471] usb-storage: device found at 56
Mar 28 07:23:39 desktop kernel: [74871.392478] usb-storage: waiting for device to settle before scanning
Mar 28 07:23:44 desktop kernel: [74876.390651] usb-storage: device scan complete
Mar 28 07:23:44 desktop kernel: [74876.392549] scsi 35:0:0:0: Direct-Access     Seagate  Desktop          0130 PQ: 0 ANSI: 4
Mar 28 07:23:44 desktop kernel: [74876.393907] sd 35:0:0:0: Attached scsi generic sg9 type 0
Mar 28 07:23:44 desktop kernel: [74876.394539] sd 35:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Mar 28 07:23:44 desktop kernel: [74876.395382] sd 35:0:0:0: [sdb] Write Protect is off
Mar 28 07:23:44 desktop kernel: [74876.395394] sd 35:0:0:0: [sdb] Mode Sense: 2f 08 00 00
Mar 28 07:23:44 desktop kernel: [74876.395401] sd 35:0:0:0: [sdb] Assuming drive cache: write through
Mar 28 07:23:44 desktop kernel: [74876.398417] sd 35:0:0:0: [sdb] Assuming drive cache: write through
Mar 28 07:23:44 desktop kernel: [74876.398430]  sdb:
Mar 28 07:23:44 desktop kernel: [74876.447386] sd 35:0:0:0: [sdb] Assuming drive cache: write through
Mar 28 07:23:44 desktop kernel: [74876.447398] sd 35:0:0:0: [sdb] Attached SCSI disk
```

---

