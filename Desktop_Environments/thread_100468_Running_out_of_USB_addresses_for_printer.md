---
title: "Running out of USB addresses for printer"
date: 2005-12-07
forum: Desktop Environments
---

### Post by ahallubuntu on 2005-12-07
I've got Ubuntu running a Samba server for an office.  It also serves as a print server, and the printer is plugged in via USB.  For various reasons, the printer gets unplugged or powered down and then restarted from time to time, and each time this happens, it seems to require a new USB address (of some sort).  Eventually, it will run out of addresses and we can no longer access the printer.

Here are the messages in the log files:

_When the printer is unplugged:_
Dec  6 15:47:55 localhost kernel: usb 1-2: usb timed out on ep0in
Dec  6 15:48:28 localhost kernel: drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -84
Dec  6 15:48:28 localhost kernel: drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk status received: -71
Dec  6 15:48:28 localhost kernel: usb 1-2: USB disconnect, address 13
Dec  6 15:48:28 localhost kernel: drivers/usb/class/usblp.c: usblp0: removed

_Then plugged back in:_
Dec  6 15:49:08 localhost kernel: usb 1-2: new full speed USB device using uhci_hcd and address 14
Dec  6 15:49:08 localhost kernel: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 14 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0217


So you can see here it used address 13 the last time and is now using 14.  I don't know at what point it runs out, but when it does, it will stop recognizing the printer.  The only way I know of to fix the problem is to re-boot, something I would like to avoid.  How can I tell the kernel to re-use old addresses or reset the count somehow without rebooting?

Any suggestions?

Thanks!

---

### Post by soulestream on 2005-12-07
you probably need to check udev rules.

soule

---

