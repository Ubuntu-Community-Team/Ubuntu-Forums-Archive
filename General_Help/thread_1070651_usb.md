---
title: "usb"
date: 2009-02-15
forum: General Help
---

### Post by Linuxmonde on 2009-02-15
how to mount usb?

---

### Post by itang sanjana on 2009-02-15
Here you go
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

HTH

---

### Post by geraldm on 2009-02-15
The usbfs (USB filesystem) is not used in newer releases such as Ibex.
Older distros did use it.  The command was
"sudo mount -t usbfs /proc/bus/usb"
That only works for older releases, and there should be a line entry in file /etc/fstab which begins with "usbfs "

For newer distros, just plug the device in.  It should be picked up, and there should be a new line for it.  Check for the device by issuing the command
"lsusb"

Gerald

---

