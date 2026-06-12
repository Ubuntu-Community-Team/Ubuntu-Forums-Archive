---
title: "USB to Serial"
date: 2007-12-24
forum: Desktop Environments
---

### Post by mjt_colo on 2007-12-24
I have installed a USB to Serial adapter and I can see in /var/log/messages where it seems to install ok....

[SIZE="2"][COLOR="Blue"]Dec 24 10:27:37 Linux-laptop kernel: [440355.712000] usb 1-1: new full speed USB device using uhci_hcd and address 5
Dec 24 10:27:37 Linux-laptop kernel: [440355.864000] usb 1-1: configuration #1 chosen from 1 choice
Dec 24 10:27:37 Linux-laptop kernel: [440355.868000] pl2303 1-1:1.0: pl2303 converter detected
Dec 24 10:27:37 Linux-laptop kernel: [440355.868000] usb 1-1: pl2303 converter now attached to ttyUSB0[/COLOR][/SIZE]

Using cutecom to write to it I get the following:
[COLOR="Blue"]
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/COLOR]

I can read from the serial port but not write to it.  Any suggestions?

---

