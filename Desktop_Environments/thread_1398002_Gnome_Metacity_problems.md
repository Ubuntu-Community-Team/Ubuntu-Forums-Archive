---
title: "Gnome Metacity problems"
date: 2010-02-03
forum: Desktop Environments
---

### Post by yester64 on 2010-02-03
Hi,
is there a way to reset the desktop to its defaults state?
For some reason i can not disable effects. If i do, all the bars disappear. I mean the titel bars from the applications and i can not switch through any application either.
So i have to have effects on to work with my desktop. It was working before but i am not sure what i did to make it behave like that.
Gnome running with Metacity 9.10.

Thanks for help.

---

### Post by SecretCode on 2010-02-04
As a one-off, try running _metacity --replace_ in a terminal or in an Alt-F2 'run application' window. Or running _gtk-window-decorator --replace_ the same way. The window decorator is the part responsible for drawing the title bars and window borders.

If that doesn't do it, try installing compizconfig-settings-manager (ccsm) and fusion-icon. Fusion-icon's menu give you a 'reload window manager' option, and ccsm gives you ways to control the appearance of the windows.

---

### Post by yester64 on 2010-02-04
I checked my log and that is what in it.

> (gnome-appearance-properties:6834): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
/usr/share/themes/Peace/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.

(gnome-appearance-properties:6834): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.2.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 

(gnome-appearance-properties:6833): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image formatUnfortunately the tips you provided did not solve it. In fact, i used the --replace command before but with no positive results.
But i thanks you for the tips.
I am not sure how to interpret the log though.

---

