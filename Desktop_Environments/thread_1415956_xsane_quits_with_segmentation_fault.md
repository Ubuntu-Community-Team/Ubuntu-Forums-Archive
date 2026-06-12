---
title: "xsane quits with segmentation fault"
date: 2010-02-25
forum: Desktop Environments
---

### Post by beausoleil on 2010-02-25
I've been fighting to get my Epson CX7800 to scan under Ubuntu 9.10.

I'm running 2.6.31-19-generic x86_64. and have libsane, sane-utils, xsane, xsane-common and libsane-extras installed. After searching these forums, I finally discovered that the /etc/sane.d/epson.conf file is deprecated and disabled in /etc/sane.d/dll.conf. I added the vendor/device number for the CX7800 to the epson2.conf file (0x4b8:0x81f), and xsane finally doesn't report no scanner found.

But it would start, then just fail with no error code. So I started it from the bash command line, and found it errors out with:```
(xsane:20103): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Segmentation fault
```There is no scanner device I can find which was created by saned (no /dev/usb/scanner0 or /dev/usbscanner0).

I've checked all the other epson threads here and find no relief. Any clues?

---

### Post by beausoleil on 2010-02-26
Bump

---

### Post by beausoleil on 2010-03-15
xsane version is 0.996, kernel is 2.6.31-20-generic. Any ideas?

---

