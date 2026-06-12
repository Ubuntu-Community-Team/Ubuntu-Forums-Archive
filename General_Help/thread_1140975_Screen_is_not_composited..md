---
title: "Screen is not composited."
date: 2009-04-28
forum: General Help
---

### Post by timstone on 2009-04-28
After upgrading to Jaunty I keep getting an error message about my screen not being composited and that I need to run Compiz (-fusion)  

well I've ran compiz in terminal and this is the output I get

```
tim@tim-desktop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

my screen resolution resets after every reboot even after changing it in the nvidia x server

can anyone help me fix this?

---

