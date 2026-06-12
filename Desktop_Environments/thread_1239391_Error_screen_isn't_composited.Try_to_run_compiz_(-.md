---
title: "Error: screen isn't composited.Try to run compiz (-fusion) or other compositing manag"
date: 2009-08-13
forum: Desktop Environments
---

### Post by Alnico on 2009-08-13
I get the following error when I boot to ubuntu:

> Error: screen isn't composited.Try to run compiz (-fusion) or other compositing manager

This is the result of running compiz in Terminal:

> Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


How do I get rid of this?

---

### Post by ronaldprettyman on 2009-08-13
> **Alnico said:**
> I get the following error when I boot to ubuntu:



This is the result of running compiz in Terminal:




How do I get rid of this?

nvidia-xconfig

---

### Post by Alnico on 2009-08-14
Errr, I get this error message:

> Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.

---

