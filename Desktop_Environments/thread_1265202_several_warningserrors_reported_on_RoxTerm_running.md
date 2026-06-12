---
title: "several warnings/errors reported on RoxTerm running Compiz"
date: 2009-09-13
forum: Desktop Environments
---

### Post by keratos on 2009-09-13
Installed barebones Ubuntu from server CD then installed Rox (session manager + desktop) and Compiz (wm)

When running compiz from within a RoxTerm the following messages appear. Any ideas how I can fix them please.
```

daz@daz-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: Plugin 'text' not loaded.

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/UbuntuStudio/background.jpg
```

Several apps requiring XGL will not run and some features of compiz are not working (like 3d cube and ring switcher)

My Video card is an IntelGMA965/GL960. Other than the few errors above, my desktop, windowing, transparency, and some compiz features DO work.

thanks

---

