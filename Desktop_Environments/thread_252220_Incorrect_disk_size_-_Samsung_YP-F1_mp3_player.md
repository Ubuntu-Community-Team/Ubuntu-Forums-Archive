---
title: "Incorrect disk size - Samsung YP-F1 mp3 player"
date: 2006-09-06
forum: Desktop Environments
---

### Post by zambizzi on 2006-09-06
When I mount it, it shows up in Nautilus and I can browse/add/remove files.  It shows up in dmesg as follows:

```

[18034038.408000] usb 5-7: new high speed USB device using ehci_hcd and address 6
[18034038.544000] scsi5 : SCSI emulation for USB Mass Storage devices
[18034038.544000] usb-storage: device found at 6
[18034038.544000] usb-storage: waiting for device to settle before scanning
[18034043.544000]   Vendor: Samsung   Model: YP-F1             Rev: 0100
[18034043.544000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[18034043.548000] SCSI device sdb: 2034432 512-byte hdwr sectors (1042 MB)
[18034043.548000] sdb: Write Protect is off
[18034043.548000] sdb: Mode Sense: 38 00 00 00
[18034043.548000] sdb: assuming drive cache: write through
[18034043.552000] SCSI device sdb: 2034432 512-byte hdwr sectors (1042 MB)
[18034043.552000] sdb: Write Protect is off
[18034043.552000] sdb: Mode Sense: 38 00 00 00
[18034043.552000] sdb: assuming drive cache: write through
[18034043.552000]  sdb: sdb1
[18034043.552000] sd 5:0:0:0: Attached scsi removable disk sdb
[18034043.552000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[18034043.552000] usb-storage: device scan complete
[18034043.912000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

However, it's showing the device as having 57.1MB of space, not the 1GB I would have expected, since there are no files on the device.  I checked hidden folders and deleted the ".trash*" file but it made no difference.  I've also run the device's built-in format function - also no difference.

When I mount it on my laptop (which uses Gentoo) it is correct w/ 1GB of available space.

What's the deal?

Thanks!

---

