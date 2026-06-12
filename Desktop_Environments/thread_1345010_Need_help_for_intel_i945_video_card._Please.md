---
title: "Need help for intel i945 video card. Please"
date: 2009-12-03
forum: Desktop Environments
---

### Post by baskar007 on 2009-12-03
I have ubuntu9.10. just one day before formatted my PC and installed ubuntu 9.10.

After that i installed all updates from update-manager. But now i can't enable Compiz in Gnome as well as KDE4.3.X .

i have tried to reinstall xorg-xserver-video-intell and many other drivers but no luck.

here i posted that error while try to enaple compiz in gnome.

any solutions???


```

baskar@baskar:~$ gnome-appearance-properties

(gnome-appearance-properties:3208): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:3209): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: 
(gnome-appearance-properties:3208): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

(gnome-appearance-properties:3208): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:3208): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:3208): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

```

---

