---
title: "Compiz on Debian?"
date: 2007-12-03
forum: Debian
---

### Post by Fixman on 2007-12-03
I tried downloading the Compiz package, but when I execute it it gives me this error:

```

martin@Debian:~$ compiz
GLX_EXT_texture_from_pixmap is available with direct rendering.

(gtk-window-decorator:4289): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:4289): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed
/usr/bin/compiz.real (core) - Fatal: No composite extension
/usr/bin/compiz: line 37:  4289 Segmentation fault      /usr/bin/gtk-window-decorator --replace
martin@Debian:~$

```

Can someone help me?

---

### Post by odiseo77 on 2007-12-21
> /usr/bin/compiz.real (core) - Fatal: No composite extension

Did you add the "Extensions" section to your /etc/X11/xorg.conf?

Open it with a text editor and add the following lines at the end of it:

```
Section "Extensions"
    Option         "Composite" "enable"
EndSection
```

In case this helps, here I attach my xorg.conf. You can borrow some parts of it, but be careful not to mess with the "Driver" line (in the "Device" section) or the "Monitor" section of your xorg.conf (if you set a bad vertical or horizontal refresh rate, you could end with a broken monitor).

Oh, and by the way, if you start compiz and get windows without borders (as it happened to me), you might want to take a look at [this]("http://bgoglin.livejournal.com/11253.html").

Hope this helps.

---

