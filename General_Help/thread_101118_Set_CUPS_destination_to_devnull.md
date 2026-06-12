---
title: "Set CUPS destination to /dev/null?"
date: 2005-12-09
forum: General Help
---

### Post by jocke on 2005-12-09
This is from instructions about [setting up the capt driver for Canon LBP-810]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-LBP-810"), but I don't know how to follow this step:
> Note that the driver talks directly to the USB port. So the printer must be connected via USB. The output destination specified in the printer spooler will not be used. If you use CUPS, set the destination to /dev/null, so that the CUPS backends do not block the USB device.
What does it mean to set the CUPS destination to /dev/null? How do I do that?

Thanx for your help! :) (I've searched through CUPS documentation for "destination" without luck)

---

### Post by kls96 on 2006-06-06
It means that you have to edit /etc/cups/printer.conf and change the Destination from usb://<something> to usb:/dev/null.

One more thing I found: the capt driver obviosly keeps trying to write to /dev/usb/lp0 which didn't exist on my system. dmesg tould me that the device was /dev/usblp0. So I created a directory /dev/usb and put a link in it: ln -s /dev/usblp0 /dev/usb/lp0. Restarted cupsys and voila, the Canon LBP-810 was working.

---

