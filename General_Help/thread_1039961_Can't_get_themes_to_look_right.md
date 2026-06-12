---
title: "Can't get themes to look right"
date: 2009-01-15
forum: General Help
---

### Post by Kivamaki on 2009-01-15
I'm trying to use this theme here for GTK2 [http://fratrip.deviantart.com/art/Gaia-Neue-Suite-100383098](http://fratrip.deviantart.com/art/Gaia-Neue-Suite-100383098)

And it's supposed to look like this: [http://fc44.deviantart.com/fs37/f/2008/284/c/c/ccc023ba724ed13ca78dabc5ad904bf9.png](http://fc44.deviantart.com/fs37/f/2008/284/c/c/ccc023ba724ed13ca78dabc5ad904bf9.png)

So I installed Emerald by (sudo apt-get install emerald) so that my borders would change, and that all worked out.

So after I downloaded the theme from deviantart, I extracted the folder and inside is the theme folder. I click and drag it into Theme tab of (System>Preferences>Appearance). And it installs and applys it. Yet it doesn't look right and I don't understand why. Here is what mine looks like, what am I doing wrong or how can I fix this? It says the required GTK2 Engine isn't installed, but I believe pixmap comes installed?

---

### Post by easybake on 2009-01-15
It looks like it really isn't applying the theme. I would use gtk-chtheme instead to apply it.

sudo apt-get install gtk-chtheme

launch it from terminal with either 
gtk-chtheme 
or 
sudo gtk-chtheme

---

### Post by Kivamaki on 2009-01-15
I installed it, and applied the theme, and it does the same thing. Although it gives this in the terminal:

> /home/hustin/.themes/Gaia Neue/gtk-2.0/gtkrc:1159: Unable to locate image file in pixmap_path: "Toolbar/toolbar.png"
/home/hustin/.themes/Gaia Neue/gtk-2.0/gtkrc:1162: Background image options specified without filename
/home/hustin/.themes/Gaia Neue/gtk-2.0/gtkrc:1159: Unable to locate image file in pixmap_path: "Toolbar/toolbar.png"
/home/hustin/.themes/Gaia Neue/gtk-2.0/gtkrc:1162: Background image options specified without filename

** (gtk-chtheme:11700): WARNING **: Pixbuf theme: Cannot load pixmap file /home/hustin/.themes/Gaia Neue/gtk-2.0/Buttons/button-prelight.png: Failed to open file '/home/hustin/.themes/Gaia Neue/gtk-2.0/Buttons/button-prelight.png': No such file or directory


(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (gtk-chtheme:11700): WARNING **: Invalid borders specified for theme pixmap:
        /home/hustin/.themes/Gaia Neue/gtk-2.0/Buttons/button-prelight.png,
borders don't fit within the image

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gtk-chtheme:11700): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

---

