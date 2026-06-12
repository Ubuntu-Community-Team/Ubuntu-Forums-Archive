---
title: "My USB MP3 works sometimes only"
date: 2006-01-15
forum: Desktop Environments
---

### Post by Bou on 2006-01-15
Hi, I bought an MP3 player a while ago, but it doesn't seem to be working fine with Ubuntu. Sometimes it does, but sometimes the system just seems not to recognise it. I'll show you the results of dmesg:

> [4294796.525000] usb 4-5: new high speed USB device using ehci_hcd and address 3[4294796.757000] SCSI subsystem initialized
[4294796.765000] Initializing USB Mass Storage driver...
[4294796.770000] scsi0 : SCSI emulation for USB Mass Storage devices

[4294796.771000] usb-storage: device found at 3
[4294796.771000] usb-storage: waiting for device to settle before scanning
[4294796.771000] usbcore: registered new driver usb-storage
[4294796.771000] USB Mass Storage support registered.
[4294796.859000] usb 4-5: USB disconnect, address 3

[4294798.025000] usb 4-5: new high speed USB device using ehci_hcd and address 4[4294798.136000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294798.140000] usb-storage: device found at 4
[4294798.140000] usb-storage: waiting for device to settle before scanning
[4294798.359000] usb 4-5: USB disconnect, address 4

[4294799.525000] usb 4-5: new high speed USB device using ehci_hcd and address 5[4294799.603000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294799.604000] usb-storage: device found at 5
[4294799.604000] usb-storage: waiting for device to settle before scanning
[4294799.859000] usb 4-5: USB disconnect, address 5

[4294801.025000] usb 4-5: new high speed USB device using ehci_hcd and address 6[4294801.103000] scsi3 : SCSI emulation for USB Mass Storage devices
[4294801.104000] usb-storage: device found at 6
[4294801.104000] usb-storage: waiting for device to settle before scanning
[4294801.359000] usb 4-5: USB disconnect, address 6

[4294802.525000] usb 4-5: new high speed USB device using ehci_hcd and address 7[4294802.603000] scsi4 : SCSI emulation for USB Mass Storage devices
[4294802.604000] usb-storage: device found at 7
[4294802.604000] usb-storage: waiting for device to settle before scanning
[4294802.859000] usb 4-5: USB disconnect, address 7

Same with address 8, 9, 10... and it goes on and on.

But sometimes it does work, and I can copy files without a problem. Why this behavior? Why failing only sometimes? :(

---

### Post by Bou on 2006-01-15
Now Nautilus suddenly recongised the drive, without me doing anything.

Dmesg:

> [4296829.106000] scsi863 : SCSI emulation for USB Mass Storage devices
[4296829.107000] usb-storage: device found at 62
[4296829.107000] usb-storage: waiting for device to settle before scanning
[4296829.359000] usb 4-5: USB disconnect, address 62
[4296830.525000] usb 4-5: new high speed USB device using ehci_hcd and address 63
[4296830.603000] scsi864 : SCSI emulation for USB Mass Storage devices
[4296830.604000] usb-storage: device found at 63
[4296830.604000] usb-storage: waiting for device to settle before scanning
[4296835.607000]   Vendor: LG        Model: MF-FE500          Rev: 0100
[4296835.607000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4296835.631000] usb-storage: device scan complete
[4296835.750000] SCSI device sda: 1003008 512-byte hdwr sectors (514 MB)
[4296835.751000] sda: Write Protect is off
[4296835.751000] sda: Mode Sense: 38 00 00 00
[4296835.751000] sda: assuming drive cache: write through
[4296835.754000] SCSI device sda: 1003008 512-byte hdwr sectors (514 MB)
[4296835.755000] sda: Write Protect is off
[4296835.755000] sda: Mode Sense: 38 00 00 00
[4296835.755000] sda: assuming drive cache: write through
[4296835.755000]  /dev/scsi/host864/bus0/target0/lun0: p1
[4296835.758000] Attached scsi removable disk sda at scsi864, channel 0, id 0, lun 0
[4296836.019000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4296847.533000] Inbound IN=eth0 OUT= MAC=00:0d:61:ae:ba:f2:00:0e:83:05:95:a4:08:00 SRC=87.126.92.214 DST=81.203.200.102 LEN=60 TOS=0x00 PREC=0x40 TTL=110 ID=49764 DF PROTO=TCP SPT=2405 DPT=4662 WINDOW=32768 RES=0x00 SYN URGP=0
[4296856.525000] Inbound IN=eth0 OUT= MAC=00:0d:61:ae:ba:f2:00:0e:83:05:95:a4:08:00 SRC=87.126.92.214 DST=81.203.200.102 LEN=60 TOS=0x00 PREC=0x40 TTL=110 ID=50654 DF PROTO=TCP SPT=2405 DPT=4662 WINDOW=32768 RES=0x00 SYN URGP=0

I'm totally puzzled. :confused:

---

