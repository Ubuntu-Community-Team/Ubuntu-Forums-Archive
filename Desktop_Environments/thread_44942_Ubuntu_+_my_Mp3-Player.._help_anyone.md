---
title: "Ubuntu + my Mp3-Player.. help anyone?"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Morimando on 2005-06-28
Okay. I got this MP3-Player and Linux recognizes it just fine. At least the 256MB onboard memory are properly treated. The problem is that the SmartMedia card i plugged into it (256MB SD (SanDisk?)) isn't recognized and thus i can't mount it. I enabled some MTD-stuff in the kernel and also i enabled the SmartMedia support that's available under "USB". Doesn't seem to work, i'm afraid ^^
Well, for starters, here's my dmesg output:

```
usb-storage: device found at 3
ohci_hcd 0000:00:02.0: wakeup
usb 2-3: new full speed USB device using ohci_hcd and address 3
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: waiting for device to settle before scanning
  Vendor: Digital   Model: MP3 Music Player  Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 04
SCSI device sdb: 501248 512-byte hdwr sectors (257 MB)
sdb: Write Protect is off
sdb: Mode Sense: 38 00 00 00
sdb: assuming drive cache: write through
SCSI device sdb: 501248 512-byte hdwr sectors (257 MB)
sdb: Write Protect is off
sdb: Mode Sense: 38 00 00 00
sdb: assuming drive cache: write through
 sdb: sdb1
Attached scsi removable disk sdb at scsi3, channel 0, id 0, lun 0
Attached scsi generic sg1 at scsi3, channel 0, id 0, lun 0,  type 0
usb-storage: device scan complete
```

Since i guess you'd also need the config of my kernel, here it is:
[http://morimando.lima-city.de/config](http://morimando.lima-city.de/config)

---

### Post by Morimando on 2005-06-28
Noone?

---

### Post by Morimando on 2005-06-29
Never mind, got it fixed at the Gentoo forum ^^
Solution is (for anyone that might encounter the same) to activate "probe all LUNs for each device" to be found under Drivers => SCSI in the kernel menu..

---

