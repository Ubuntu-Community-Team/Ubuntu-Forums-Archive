---
title: "Novatel Ovation U727 in USB Hub"
date: 2009-03-08
forum: General Help
---

### Post by ba_rich on 2009-03-08
When a U727 is plugged into the USB port on the front of the PC, it is recognized immediately and the ttyUSB devices are created.

If a USB hub is plugged into the USB port on the front of the PC and the U727 is plugged into the hub, it takes over 7 minutes for the ttyUSB devices to be created. The dmesg contents are below.

The PC is running Ubuntu 8.10. The kernel is 2.6.27-11.

What causes the delay in creating the ttyUSB devices when using the USB Hub?


[ 1685.600186] usb 5-6.5: new full speed USB device using ehci_hcd and address 8
[ 1685.694790] usb 5-6.5: configuration #1 chosen from 1 choice
[ 1685.698868] scsi9 : SCSI emulation for USB Mass Storage devices
[ 1685.704460] usb-storage: device found at 8
[ 1685.704475] usb-storage: waiting for device to settle before scanning
[ 1690.704420] usb-storage: device scan complete
[ 1690.705881] scsi 9:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
[ 1690.720879] sr1: scsi-1 drive
[ 1690.721169] sr 9:0:0:0: Attached scsi CD-ROM sr1
[ 1690.721447] sr 9:0:0:0: Attached scsi generic sg6 type 5
[ 1690.946749] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1690.946790] sr: Sense Key : No Sense [current]
[ 1690.946799] sr: Add. Sense: No additional sense information
[ 1751.056229] usb 5-6.5: reset full speed USB device using ehci_hcd and address 8
[ 1751.199279] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1751.199317] sr: Sense Key : No Sense [current]
[ 1751.199328] sr: Add. Sense: No additional sense information
[ 1811.296145] usb 5-6.5: reset full speed USB device using ehci_hcd and address 8
[ 2117.104951] usb 5-6.5: USB disconnect, address 8
[ 2118.328169] usb 5-6.5: new full speed USB device using ehci_hcd and address 9
[ 2118.422465] usb 5-6.5: configuration #1 chosen from 1 choice
[ 2118.423176] option 5-6.5:1.0: GSM modem (1-port) converter detected
[ 2118.423505] usb 5-6.5: GSM modem (1-port) converter now attached to ttyUSB0
[ 2118.424432] option 5-6.5:1.1: GSM modem (1-port) converter detected
[ 2118.424656] usb 5-6.5: GSM modem (1-port) converter now attached to ttyUSB1
[ 2118.425483] option 5-6.5:1.2: GSM modem (1-port) converter detected
[ 2118.425807] usb 5-6.5: GSM modem (1-port) converter now attached to ttyUSB2
[ 2118.426794] option 5-6.5:1.3: GSM modem (1-port) converter detected
[ 2118.427086] usb 5-6.5: GSM modem (1-port) converter now attached to ttyUSB3
[ 2118.428843] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2118.437407] usb-storage: device found at 9
[ 2118.437429] usb-storage: waiting for device to settle before scanning
[ 2123.436538] usb-storage: device scan complete
[ 2123.438605] scsi 10:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[ 2123.446073] sd 10:0:0:0: [sdf] Attached SCSI removable disk
[ 2123.447671] sd 10:0:0:0: Attached scsi generic sg6 type 0

---

### Post by ba_rich on 2009-03-08
The U727 is a strange device. When it is first plugged in, it shows up as a storage device. If you manually eject the storage device, the ttyUSB devices show up shortly after the eject.

If you don't manually eject the devices, the ttyUSB devices show up eventually (7-9 minutes).

Maybe run a script at startup to look for and eject the storage devices?

---

