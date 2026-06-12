---
title: "Compiz not working in Ubuntu Karmic"
date: 2009-12-04
forum: Desktop Environments
---

### Post by new_penguin on 2009-12-04
Strangely, I've upgraded to 9.10, and Compiz is not working anymore! Here's what happens:

```
root@david-desktop:/home/david# compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: xterm 
no xterm found, exiting

```The graphics card is:

```
root@david-desktop:/home/david# lspci -v | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

```

---

### Post by Confuzius on 2009-12-04
If you've done an upgrade there's a chance that your kernel and video card kernel module don't match up.
Try uninstalling and re-installing your video drivers.

---

### Post by new_penguin on 2009-12-05
I reinstalled the video drivers, and still no luck.

Again, this is what happened:

```
david@david-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by MelDJ on 2009-12-05
did you get the driver form the ati website or hardware drivers. i find the driver from the ati website is more reliable

---

### Post by new_penguin on 2009-12-06
I got the fglrx drivers through synaptic, along with that the ATI drivers will not install.

---

