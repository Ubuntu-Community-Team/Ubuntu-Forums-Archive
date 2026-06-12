---
title: "Can't use Ti-84"
date: 2009-02-19
forum: General Help
---

### Post by WIndows to LInux on 2009-02-19
I installed TiLP2 and tried to connect my Ti-84, this is the cmd output running a root terminal

ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted

(tilp:5305): ticables-WARNING **: no devices found!

tilp-INFO: tilp_device_err catched error 37

It was pluged in
Do I need the kernel modules??
This is the main thing that is keeping me from giving Windows the boot

---

### Post by WIndows to LInux on 2009-03-07
I've also had problems installing the USB (silverlink) kernel module

---

### Post by WIndows to LInux on 2009-05-07
Has the Ubuntu devlopement team done anything about this? Shouldn't the kernel module be a dependancy?

This is one of the few reasons that I keep a copy of Windows XP (may be upgrading to 7)

---

### Post by Arrorn on 2009-05-15
I use 

```
sudo tilp
```

that works for me..

---

### Post by WIndows to LInux on 2009-05-26
why would typing sudo be any different than using a root terminal?

sudo gives you (for a time) root privileges

---

### Post by WIndows to LInux on 2009-07-24
Tried the new version of tilp2, which came with some drivers

in root terminal:

ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted

(tilp:5804): ticables-Warning**: no devices found!

Msg: failed to open USB device.
Cause: check your USB cable is plugged and/or the calculator is ON! Check your libusb and usbfs permissions, too.
System: Inappropriate ioctl for device (errno = 25)


the calculator is connected and turned on, should this be reported as a bug in launchpad?

---

