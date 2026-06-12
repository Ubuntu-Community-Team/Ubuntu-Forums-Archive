---
title: "U3 Puzzle with Dapper"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Dana on 2006-09-13
I have a Memorex U3 Travel Drive that is not playing well with Ubuntu (Dapper). It of course works under Windows. I do not expect this device to function as a U3 UBS device in the OS environment but all I've read indicates the data partition of the device should appear to Linux as any other USB memory device. It's not happening. A few weeks ago when I tried it the U3 partition was recognized as a CD device as it perhaps should be. It took several minutes.But the data partition was never recognized. Now it is not even picked up as a CD device. Last night I read something that told me if the data partition is password protected it will not work with Linux. I removed the pw protection but the results are the same.

Further experimentation shows the U3 drive is recognized mabye 1 out of 100 times it is inserted. Tonight I had it in for 15 minutes with nothing happening. While I was opening Synaptic the drive was suddenly recognized at"
dana@ubuntu:~$ ls -l /dev/sd*
brw-rw---- 1 root plugdev 8, 0 2006-09-13 19:33 /dev/sda
brw-rw---- 1 root plugdev 8, 1 2006-09-13 19:33 /dev/sda1

Other regular USB memory sticks work.
Below is some of what I see with dmesg if the drive is not recognized:

[4298405.495000] usb 1-1: new full speed USB device using uhci_hcd and address 1 27
[4298405.995000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4298406.429000] cdrom: open failed.
[4298406.440000] cdrom: open failed.
[4298406.495000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[4298406.995000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[4298407.495000] usb 1-1: new full speed USB device using uhci_hcd and address 5
[4298407.995000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[4298408.495000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[4298408.995000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[4298409.495000] usb 1-1: new full speed USB device using uhci_hcd and address 9
[4298409.995000] usb 1-1: new full speed USB device using uhci_hcd and address 1 0

My ThinkPad is USB 1.1  and the U3 drive is USB 2.

When the U3 drive was recognized tonight dmesg output was:

[4296119.303000] SCSI subsystem initialized
[4296119.389000] Initializing USB Mass Storage driver...
[4296119.391000] scsi0 : SCSI emulation for USB Mass Storage devices
[4296119.391000] usb-storage: device found at 40
[4296119.391000] usb-storage: waiting for device to settle before scanning
[4296119.392000] usbcore: registered new driver usb-storage
[4296119.392000] USB Mass Storage support registered.
[4296124.395000]   Vendor: Memorex   Model: Mini TravelDrive  Rev: 6.15
[4296124.395000]   Type:   Direct-Access                      ANSI SCSI revision: 00[4296124.399000]   Vendor: Memorex   Model: Mini TravelDrive  Rev: 6.15
[4296124.399000]   Type:   CD-ROM                             ANSI SCSI revision: 00[4296124.407000] usb-storage: device scan complete
[4296124.590000] Driver 'sd' needs updating - please use bus_type methods
[4296124.599000] SCSI device sda: 1994751 512-byte hdwr sectors (1021 MB)
[4296124.603000] sda: Write Protect is off
[4296124.603000] sda: Mode Sense: 45 00 00 08
[4296124.603000] sda: assuming drive cache: write through
[4296124.617000] SCSI device sda: 1994751 512-byte hdwr sectors (1021 MB)
[4296124.621000] sda: Write Protect is off
[4296124.621000] sda: Mode Sense: 45 00 00 08
[4296124.621000] sda: assuming drive cache: write through
[4296124.621000]  sda: sda1
[4296124.632000] sd 0:0:0:0: Attached scsi removable disk sda
[4296124.671000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4296124.672000] sr 0:0:0:1: Attached scsi generic sg1 type 5
[4296124.696000] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[4296124.698000] sr 0:0:0:1: Attached scsi CD-ROM sr0
[4296127.622000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4296129.221000] UDF-fs: No VRS found
[4296129.305000] UDF-fs: No VRS found
[4296129.373000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4296129.379000] ISOFS: changing to secondary root
[4296140.692000] CSLIP: code copyright 1989 Regents of the University of California
[4296140.710000] PPP generic driver version 2.4.2
[4296142.210000] PPP BSD Compression module registered
[4296142.299000] PPP Deflate Compression module registered

---

