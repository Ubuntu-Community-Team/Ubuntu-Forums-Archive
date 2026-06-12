---
title: "AMD64: Gnome Appearance Properties defaulting to no visual effects"
date: 2010-05-17
forum: Desktop Environments
---

### Post by bcschmerker on 2010-05-17
I recently upgraded from 8.04.4 to 10.04 on my original PATA hard drives (/home using ext3, balance of installation using ext4) and found that GNOME Appearance Properties fails to remember Visual Effects settings, defaulting to None where I expect Basic.  This issue affects all user applications.  What specific files, if any, could contribute to this issue?

---

### Post by lukeiamyourfather on 2010-05-17
Do you have a graphics driver installed that supports 3D acceleration? If not, then that's probably the first place to start since its a requirement for the desktop effects. Cheers!

---

### Post by bcschmerker on 2010-05-17
My installation already packs the ATI/AMD FGLRX driver, which the planar ATI Radeon HD 3200 on my Everex' Gigabyte MA78GM-S2HP (Advance Micro Devices 780G chipset) requires for full performance with my 1440x900px LCD display unit.

---

### Post by lukeiamyourfather on 2010-05-18
Have you confirmed the driver is actually in use? In a terminal run this to see what renderer is being used.

```
glxgears -info
```

It should say something FGLRX as the renderer. If it says software then its not using the driver.

---

### Post by bcschmerker on 2010-05-18
> **lukeiamyourfather said:**
> Have you confirmed the driver is actually in use? In a terminal run this to see what renderer is being used.

```
glxgears -info
```

It should say something FGLRX as the renderer. If it says software then its not using the driver.
No dice for a /usr/bin/glxgears, as I need the mesa-utils package; I'll see what effect, if any, it has on the default to no effects....

Update:  No effect initially after a reboot, still must activate Basic effects manually in GNOME Appearance Properties.  From GNOME Terminal, GLXGears repeats VDA commands to StdOut, terminates with an error exit status upon force-closing the window that GLXGears opens.

Update 2:  Possible bug in GDK, as, when activating GNOME Appearance Properties from GNOME Terminal, the following StdErr occurs:
```
(gnome-appearance-properties:2166): Gdk-CRITICAL **: gdk_display_sync: assertion 'GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:2166): Gdk-CRITICAL **: gdk_display_sync: assertion 'GDK_IS_DISPLAY (display)' failed
```

---

### Post by bcschmerker on 2010-07-10
When upgrading from previous versions of Ubuntu, watch out for incompatible data across account hidden files---that's apparently what tripped me up to begin with.  After saving my User profile directory from /home to a USB memory chip of suitable size, I re-installed 10.04, which reinitialized all hidden files properly; the only hidden subdirectory I transferred back to my reinstalled User profile from said USB chip was .mozilla (used by Mozilla Firefox 3.6.*).

---

