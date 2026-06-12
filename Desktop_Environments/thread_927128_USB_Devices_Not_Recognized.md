---
title: "USB Devices Not Recognized"
date: 2008-09-22
forum: Desktop Environments
---

### Post by mlitteken on 2008-09-22
Hey all,
I'm running Hardy Heron Desktop 8.04 on a Compaq Presario 6000 and no usb devices are recognized by it. They are being powered up (optical mouse lights up when plugged in) but they aren't being seen by the system. I've searched and read the forums here without much luck. USB bus drivers are being loaded.

Here are the results of 'lspci -v':

```
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9012
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d400 [size=32]
	Capabilities: [80] Power Management version 2

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9012
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d800 [size=32]
	Capabilities: [80] Power Management version 2

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9012
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at dc00 [size=32]
	Capabilities: [80] Power Management version 2

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9012
	Flag
s: bus master, medium devsel, latency 32, IRQ 19
	Memory at ef001000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

```

And here is a snippet from dmesg that shows the errors being thrown:
 
```
[ 1275.738735] usb 4-5: new high speed USB device using ehci_hcd and address 6
[ 1291.286251] usb 4-5: device not accepting address 6, error -110
[ 1298.806176] usb 4-5: new high speed USB device using ehci_hcd and address 8
[ 1314.353699] usb 4-5: device not accepting address 8, error -110

```

---

### Post by Kanga on 2009-01-12
Having just upgraded to Hardy Heron from Dapper Drake, I find that my printer and my usb hub do not work.
This isnt much good to me, I'm thinking of trying Fedora 10. It may recognise the hardware better.
Isnt there a fix for this problem, please ?:confused:

---

