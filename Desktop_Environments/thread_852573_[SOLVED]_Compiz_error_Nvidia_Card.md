---
title: "[SOLVED] Compiz error Nvidia Card"
date: 2008-07-07
forum: Desktop Environments
---

### Post by cane1832 on 2008-07-07
so when i run compiz it gives me this error and don't know where to go from here any input is apprietiated thank you.
Nvidia Card : 7950gt
OS : Hardy 8.04
Driver is the Ristricted one

~$ compiz -help
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0295 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3360x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-help'

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by Fingers &amp; Thumbs on 2008-07-07
check synaptic package manager to see which nvidia driver is installed. I "THINK" that the correct driver for your card is "nvidia-glx-new" if this is selected try a reinstallation of ths driver.

---

