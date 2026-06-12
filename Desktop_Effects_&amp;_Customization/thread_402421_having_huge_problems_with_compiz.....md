---
title: "having huge problems with compiz...."
date: 2007-04-05
forum: Desktop Effects &amp; Customization
---

### Post by searayman on 2007-04-05
so i came home and my computer was logged out which it never is... so i logged back in and compiz wouldnt start. I tried to re-install drivers with envy thinkign maybe they were messed up durign an update. I use ubuntu edgy eft by the way. SO i tried to start compiz and i got this:

mike@mike-desktop:~$  gtk-window-decorator --replace &
[1] 10215
mike@mike-desktop:~$ 
(gtk-window-decorator:10215): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:10215): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

---

