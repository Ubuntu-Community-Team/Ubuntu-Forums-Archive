---
title: "Which driver for a 5200 GO to enable effects?"
date: 2007-12-12
forum: Desktop Effects &amp; Customization
---

### Post by chauncey on 2007-12-12
Sorry if this has been answered before, but this has been hounding me for the past week.  I have a Toshiba M200 Tablet PC running Ubuntu Gutsy (7.10)  on a fresh install I did this morning.  There are 3 available nvidia drivers that I can see in the Add/Remove programs manager.  There is a binary driver, a "new" driver, and a "legacy" driver.  Which of these should I install for an nVidia 5200 GO, so that I can enable desktop effects?  I have installed and enabled the Restricted nVidia driver as well.

---

### Post by naja on 2007-12-12
Hi
go to System------Administration------Restirected Driver Manger and it will install the right driver

---

### Post by chauncey on 2007-12-12
Thank you for the quick reply, however, when I do that the Restricted Driver installs and enables fine, but when I attempt to enable Visual Effects I get a pop-up error that reads: "Desktop effects could not be enabled"

The "NVidia binary  X.Org driver ('new' driver)" is installed, according to the add/remove programs list.

---

### Post by PinkFloyd102489 on 2007-12-12
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run)

---

### Post by chauncey on 2007-12-12
> **PinkFloyd102489 said:**
> [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run)

How should I install this?  When I try to do it when booted into recovery mode, I get lots of errors.

---

### Post by Iwantu_ubuntu on 2007-12-12
Go to Synaptic Package Manager and install xgl-server...I believe I had the same error message too.  Also install Compiz Advanced Desktop Effects.

---

### Post by dpar on 2007-12-13
Restricted drivers should be fine for the 5200.
Install ccsm (compizconfig-settings-manager) from the repos. You will usually get that error if ccsm isn't installed.

---

