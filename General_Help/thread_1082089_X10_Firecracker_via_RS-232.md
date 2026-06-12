---
title: "X10 Firecracker via RS-232"
date: 2009-02-27
forum: General Help
---

### Post by mastermindg on 2009-02-27
I'm working on a Dell E521 (no serial ports). I've got the X10 CM17A Firecracker device attached to an RS-232 USB to Serial dongle. I've setup the usbserial module as described [**here**]("http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html").

I checked dmesg are there are no errors related to this, just the correct output recognizing the module:

```
[113830.887118] ch341 1-8:1.0: ch341-uart converter detected
[113830.943656] usb 1-8: ch341-uart converter now attached to ttyUSB0
```

My problem is that when I attempt to access the device via bottlerocket is get this:

```
$ br -x /dev/ttyUSB0 -F
br: error: [Invalid argument] ioctl
```

How can I troubleshoot this issue?

---

