---
title: "Bug in Kubuntu with printing?"
date: 2005-07-09
forum: Desktop Environments
---

### Post by dejitarob on 2005-07-09
In Gnome my printer (HP PSC1315) worked fine. I installed Kubuntu and my printer stopped working. Whenever I tried to print something, the printer would go offline. I checked /var/log/cups/error_log and saw *Unable to open USB device "usb://hp/psc%201310%20series%20?serial=CN47FB108TO2": No such device*. So I opened up the /etc/cups/printers.conf file and changed the DeviceURI line from *usb://hp/psc%201310%20series%20?serial=CN47FB108TO2* to */dev/usb/lp0*. It now works fine. It seems like they are a handful of threads with similar circumstances, many of them left unresolved.

---

### Post by chandra on 2005-07-10
Try setting permissions so:

sudo chmod a+rw /dev/usb/lp0

and see if you can print.

I think this is a bug that has somehow crept in after the Hoary release via some upgraded package(s).

---

