---
title: "Install kubuntu via usb?"
date: 2006-05-25
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-05-25
Can I put a kubuntu iso file onto a usb disk and somehow boot off of it and install?

I have no cd's for burning right now, and i need this done as quick as possible. (If it is possible, that is)

Thanks.

---

### Post by aysiu on 2006-05-25
You can install Damn Small Linux to a USB and boot off it...

I don't think this can be done with Kubuntu.

---

### Post by [S|G] on 2006-05-25
I haven't really tested it, but this might work:

1 - Use a fresh USB drive (with no files on it)
2 - use the following command:
```

dd if=kubuntu.iso of=/dev/UsbDevice

```
3 - Configure your BIOS to boot from USB device.

Replace /dev/UsbDevice with the appropriate device (such as /dev/sda1). Be sure to tell us wether it works or not.

---

### Post by stiankarlsen on 2006-05-25
No go, though it might be the ipod I use as the usb disk. (Had some trouble with the format)

I'll be giving it another shot later on tonight, gonna get my hands on another usb disk.

I'll get back to you guys.

---

