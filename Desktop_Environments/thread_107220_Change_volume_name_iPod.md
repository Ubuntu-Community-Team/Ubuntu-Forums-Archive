---
title: "Change volume name iPod"
date: 2005-12-22
forum: Desktop Environments
---

### Post by slazh on 2005-12-22
I've been looking into this for a while now, but I can't seem to find a solution for the 'problem'; evertyime my ipod mini gets mounted, it gets the volume name "IPOD-DELTA". 

Is it possible to change this, and where should I configure this?
The HAL device manager shows some info when the ipod is mounted,
but I can't change a thing there.

dmesg output:
```
usb 4-4: new high speed USB device using ehci_hcd and address 6
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: p1 p2
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete
```

---

### Post by mjunior on 2006-05-26
Are you using gtkpod? If you do so, try simple retype the ipod's name on the left tab and press sync...

---

