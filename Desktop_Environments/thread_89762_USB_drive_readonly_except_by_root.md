---
title: "USB drive readonly except by root"
date: 2005-11-13
forum: Desktop Environments
---

### Post by Jemm on 2005-11-13
I've searched and tinkered for days with no luck.

My USB drive automounts fine but no matter what I do, I can't get it to mount read-write for users.  It is read-only for all except root.

Thanks in advance for any advice.

Details:
ADS Tech USB 2 enclosure
[http://www.adstech.com/products/USBX_835/intro/USBX835_intro.asp?pid=USBX835](http://www.adstech.com/products/USBX_835/intro/USBX835_intro.asp?pid=USBX835)
Western Digital WD3200JB 320 GiB drive

------------ dmesg when plugging in device
usb 5-4: new high speed USB device using ehci_hcd and address 4
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: WDC WD32  Model: 00JB-00KFA0       Rev:  0 0
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
sda: assuming drive cache: write through
SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
sda: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: p1 p2
Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete
----------- end dmesg

---

### Post by aysiu on 2005-11-13
What's the output of these two commands? ```
sudo fdisk -l
``` ```
cat /etc/fstab
```

---

