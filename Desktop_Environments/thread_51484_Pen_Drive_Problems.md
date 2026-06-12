---
title: "Pen Drive Problems"
date: 2005-07-24
forum: Desktop Environments
---

### Post by celinek on 2005-07-24
I'm not beeing able to mount my pen drive or my mass storage camera. When I did it before an icon appears automaticaly in my desktop. A few days ago I don't know what happened but that icon does not show anymore. I've tried to mount it manualy with mount /dev/sda1 /mnt/pendrive (I've created this directory of course) but the system says that the special device /dev/sda1 does not exist. Yes I've checked under /dev and there is no sda or sda1 or anything like that. The only place where i can find my pen drive and my camera correctly listed is in /proc/bus/usb/devices what means, I think, that the system recognizes the devices some how. 
Can you help to solve this problem?

---

### Post by PeP on 2005-07-24
the dmesg  command will show you where your pen drive is:

myne gives me that
 > scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: SONY      Model: Storage Media     Rev: 1.00
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sda: 507904 512-byte hdwr sectors (260 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 507904 512-byte hdwr sectors (260 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
usb-storage: device scan complete


you may have another location (sdb, sdc, sdd ...) then try to mount sdb1, sdc1, sdd1 ...

---

