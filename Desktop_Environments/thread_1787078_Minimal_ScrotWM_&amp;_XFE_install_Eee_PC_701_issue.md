---
title: "Minimal ScrotWM &amp; XFE install Eee PC 701 issues."
date: 2011-06-20
forum: Desktop Environments
---

### Post by casbahdk on 2011-06-20
I have just installed a minimal Ubuntu 10.04 system with ScrotWM and the XFE file manager on an Eee PC 701. There seem to be two scripts not installed and I can't seem to find them. The first is the script for adding repositories using the add-apt-repository command. The second is the automatic mounting of USB pen drives and other external drives when they get connected as in a normal Ubuntu desktop install. I have tried editing /etc/fstab by adding the individual drive's UUID but this is a pain when you have 10 usb pen drives, a couple of external drives and/or if you want to connect a friends drive. Even if it succeeds it only works running in root (sudo).

Anyone have a solution for either of these issues?

---

### Post by kerry_s on 2011-06-20
1. software-properties-gtk

2. gvfs

---

### Post by casbahdk on 2011-06-21
> **kerry_s said:**
> 1. software-properties-gtk

2. gvfs

Cheers. GVFS is supposed to automatically mount connected USB drives? I still can't get the drives mounted. Is there some configuration that I am missing?

---

### Post by kerry_s on 2011-06-21
> **casbahdk said:**
> Cheers. GVFS is supposed to automatically mount connected USB drives? I still can't get the drives mounted. Is there some configuration that I am missing?

yeah, i think the file manager has to support auto mounting to use it.

try "usbmount" sounds like what your looking for.

---

### Post by casbahdk on 2011-06-21
> **kerry_s said:**
> yeah, i think the file manager has to support auto mounting to use it.

try "usbmount" sounds like what your looking for.

Cheers. usbmount didn't work. However, when I uninstalled xfe and installed PCmanFM as file manager, HAL was also installed. Now usbmount works with both PCmanFM and Xfe, but on reboot, the drive can only be accessed from Xfe, by logging in as root, while this isn't a problem in PCmanFM. Weird.

---

