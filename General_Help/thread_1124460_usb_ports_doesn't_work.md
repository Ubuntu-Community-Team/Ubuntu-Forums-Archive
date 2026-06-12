---
title: "usb ports doesn't work"
date: 2009-04-13
forum: General Help
---

### Post by ultratt on 2009-04-13
I have 2 usb ports in front and 2 at the back. Today all the sudden only one of the port at the back is working. The rest do not work. Won't detect my usb drive. And I found lots of error with dmesg

[  421.952022] hub 3-0:1.0: connect-debounce failed, port 1 disabled

The one is working have

[  439.248020] usb 3-1: new high speed USB device using ehci_hcd and address 6
[  439.432835] usb 3-1: configuration #1 chosen from 1 choice
[  439.433698] scsi5 : SCSI emulation for USB Mass Storage devices
[  439.434090] usb-storage: device found at 6
[  439.434094] usb-storage: waiting for device to settle before scanning
[  444.432265] usb-storage: device scan complete

uname -a 
Linux dev12 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

ubuntu 8.10

any idea?

---

