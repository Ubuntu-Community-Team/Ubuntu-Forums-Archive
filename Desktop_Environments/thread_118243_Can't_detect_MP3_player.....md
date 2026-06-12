---
title: "Can't detect MP3 player...."
date: 2006-01-16
forum: Desktop Environments
---

### Post by Durham on 2006-01-16
I'm not able to detect my Asono Mica mp3 player.

lsusb tells me this:

> [SIZE="2"]$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000[/SIZE]

dmesg | tail shows this:

> [SIZE="2"]$ dmesg|tail
[4997801.977000] usb 3-2: can't set config #1, error -71
[4997802.879000] usb 3-2: new full speed USB device using uhci_hcd and address 82
[4997803.536000] usb 3-2: can't set config #1, error -71
[4997803.603000] usb 3-2: new full speed USB device using uhci_hcd and address 83
[4997803.678000] usb 3-2: device descriptor read/64, error -71
[4997803.852000] usb 3-2: device descriptor read/64, error -71
[4997804.015000] usb 3-2: new full speed USB device using uhci_hcd and address 84
[4997804.423000] usb 3-2: device not accepting address 84, error -71
[4997804.487000] usb 3-2: new full speed USB device using uhci_hcd and address 85
[4997804.895000] usb 3-2: device not accepting address 85, error -71[/SIZE]

fdisk -l tell me this:

> [SIZE="2"]$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14215   114181956   83  Linux
/dev/hda2           14216       14593     3036285    5  Extended
/dev/hda5           14216       14593     3036253+  82  Linux swap / Solaris[/SIZE]

> $ uname -orv
2.6.12-10-386 #1 Fri Nov 18 11:51:02 UTC 2005 GNU/Linux

> $ lsmod|grep usb
usbcore               104316  3 ehci_hcd,uhci_hcd

---

