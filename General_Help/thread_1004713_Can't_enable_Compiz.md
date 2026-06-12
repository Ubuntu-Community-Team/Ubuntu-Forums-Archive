---
title: "Can't enable Compiz"
date: 2008-12-07
forum: General Help
---

### Post by ace214 on 2008-12-07
I can't seem to enable Compiz. I had it enabled, and the last event I can think of was connecting my machine to a projector. I have since reconfigured xorg to the default and it still doesn't work. This is the terminal output.

> There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


---

### Post by gettinoriginal on 2008-12-07
First of all, System > Preferences > Appearance > Visual Effects, which is checked.
Second, System > Admin > Hardware Drivers

Sometimes when I do something to my system, for whatever reason, it moves me to None or Normal on visual effects.

---

### Post by ace214 on 2008-12-07
The previous terminal output is what happens when I try to move it from None to Normal. There are no third-party drivers for this system- it has Intel integrated graphics.

---

