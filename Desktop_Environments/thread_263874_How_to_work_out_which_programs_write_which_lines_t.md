---
title: "How to work out which programs write which lines to /var/log/messages"
date: 2006-09-23
forum: Desktop Environments
---

### Post by SpacePony on 2006-09-23
I'm trying to work out which programs in Ubuntu write certain lines to the /var/log/messages. In particular I would like to figure out which program is responsbile for writing the following:

```

Sep 24 10:08:14 localhost kernel: [17182145.312000] usb 4-3: USB disconnect, address 4
Sep 24 10:08:15 localhost kernel: [17182147.068000] usb 4-3: new high speed USB device using ehci_hcd and address 5
Sep 24 10:08:16 localhost kernel: [17182147.200000] scsi2 : SCSI emulation for USB Mass Storage devices
Sep 24 10:08:20 localhost kernel: [17182152.200000]   Vendor: ST940811  Model: 4A                Rev:  0 0
Sep 24 10:08:20 localhost kernel: [17182152.200000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Sep 24 10:08:20 localhost kernel: [17182152.200000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
Sep 24 10:08:20 localhost kernel: [17182152.204000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
Sep 24 10:08:20 localhost kernel: [17182152.204000]  sdb: sdb1 sdb3
Sep 24 10:08:20 localhost kernel: [17182152.228000] sd 2:0:0:0: Attached scsi disk sdb
Sep 24 10:08:20 localhost kernel: [17182152.228000] sd 2:0:0:0: Attached scsi generic sg0 type 0
Sep 24 10:08:21 localhost usbmount[7677]: executing command: mount -text2 -osync,noexec,nodev,noatime,gid=4001,umask=0707 /dev/sdb1 /media/usb0
Sep 24 10:08:51 localhost kernel: [17182182.864000] usb 4-3: reset high speed USB device using ehci_hcd and address 5
Sep 24 10:08:52 localhost usbmount[7677]: executing command: run-parts /etc/usbmount/mount.d
Sep 24 10:09:22 localhost kernel: [17182213.428000] usb 4-3: reset high speed USB device using ehci_hcd and address 5
Sep 24 10:09:52 localhost kernel: [17182243.748000] usb 4-3: reset high speed USB device using ehci_hcd and address 5
Sep 24 10:10:23 localhost kernel: [17182274.388000] usb 4-3: reset high speed USB device using ehci_hcd and address 5
Sep 24 10:10:58 localhost kernel: [17182309.448000] usb 4-3: reset high speed USB device using ehci_hcd and address 5
Sep 24 10:10:58 localhost kernel: [17182309.620000] sd 2:0:0:0: SCSI error: return code = 0x50000
Sep 24 10:10:58 localhost kernel: [17182309.620000] end_request: I/O error, dev sdb, sector 45017460
Sep 24 10:10:58 localhost kernel: [17182309.620000] end_request: I/O error, dev sdb, sector 45017461
Sep 24 10:11:59 localhost kernel: [17182371.016000] usb 4-3: reset high speed USB device using ehci_hcd and address 5
Sep 24 10:12:00 localhost kernel: [17182371.648000] usb 4-3: reset high speed USB device using ehci_hcd and address 5


```

And then the next question after finding out which program (or is it the kernel itself?) writes those lines is 'Where do I find the documentation that tells me what the stuff in those lines really means?'

---

### Post by Zwack on 2006-09-23
Ummm  the program that writes in /var/log/messages is usually syslogd (although klogd helps...)

But that's probably not what you meant.

In the example you gave there are two separate things writing.  The kernel (the lines that start <date> localhost kernel) and usbmount (the other two)

The Kernel lines are written by different modules and actuially tell you which part of the kernel is responsible.  

Reading the excerpt I see a USB device being plugged in.  It's a Seagate ST940811 Drive (and the SCSI emulation for USB mass storage devices is loaded)...

It's identified as sdb and sg0 and has two partitions (sdb1 and sdb3)...

It's mounted with usbmount, then four resets appear and then a SCSI error, then two I/O errors and then two more resets...

The kernel documentation would be the place to start looking for more info.

I hope that this helps,

Z.

---

