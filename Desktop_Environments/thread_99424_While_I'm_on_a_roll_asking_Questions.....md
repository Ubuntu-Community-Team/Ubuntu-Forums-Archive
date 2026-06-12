---
title: "While I'm on a roll asking Questions...."
date: 2005-12-05
forum: Desktop Environments
---

### Post by rshol on 2005-12-05
What are the usb ports called in kubuntu 5.10?  I downloaded kpilot, pluged in my treo and it is not autodetected at all.  It looks in /dev/pilot, mepis liked /dev/ttyUSB0 (or 1 or 2 or whatever), but nothing for kubuntu.  When I do "lsmod | grep usb" I get

usbhid                 35264  0
usbcore               118044  3 usbhid,uhci_hcd

so it "looks" like there is usb support (besides my usb mouse is detected).

Thanks.

---

### Post by metoo on 2005-12-06
Cannot really help you, but have you looked in /dev/usb ?

lsusb or 'lsusb -v' tells you what the kernel sees (which is not always forwarded to userland).

---

