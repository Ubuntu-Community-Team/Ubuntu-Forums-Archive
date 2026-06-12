---
title: "Identical printers mixed up"
date: 2009-01-29
forum: General Help
---

### Post by nagylzs on 2009-01-29
Hi, we have a printer server with three identical printers (Epson R285). We are using them for different tasks: one is for printing invoices, the other is a photo printer and the third one has sublimation ink in it. When we restart the computer, all printers are mixed up. Well, just mixed up but all logical printer prints to the same physical printer...

It is probably because they are of the same type. How can I specify that which physical printer belongs to what printer setting? I was looking at /etc/cups/* but apparently the device specified in the config file is something like

DeviceURI usb://EPSON/Stylus%20Photo%20R285

(in other words, it is not a physical USB device name...)

Thanks

---

### Post by nagylzs on 2009-02-11
OK, so no answer on this? Should I post a bug report?

---

