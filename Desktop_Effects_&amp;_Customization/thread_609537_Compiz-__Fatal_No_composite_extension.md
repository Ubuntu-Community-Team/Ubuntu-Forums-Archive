---
title: "Compiz-  Fatal: No composite extension"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by Imashinu on 2007-11-11
So I am pretty sure I have my ATI drivers installed properly after reading some tutorials for Ubuntu 7.10 and now im getting this weird error

imashinu@imashinu-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA:        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 0300: 1002:5954 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:6992): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:6992): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
/usr/bin/compiz.real (core) - Fatal: No composite extension

---

### Post by jimerickso on 2007-11-11
you could try making sure that the composite extension is enabled in /etc/X11/xorg.conf. i am not sure what all the pixmap stuff is about.

---

