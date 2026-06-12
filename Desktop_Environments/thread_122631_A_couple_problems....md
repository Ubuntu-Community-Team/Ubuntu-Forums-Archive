---
title: "A couple problems..."
date: 2006-01-28
forum: Desktop Environments
---

### Post by katiad on 2006-01-28
So, I recently did two things to alter my system - I installed gtk2-engines-gtk-qt to fix my small fonts problem, and then I upgraded to kde3.5.

Now gnome will not load - it gets to where it appears to be setting up the desktop, then goes gray and makes distorted warning beeps. No error message pops up, and I end up having to reboot the entire computer. Not that this is a /huge/ problem, since I don't really use gnome all that often... if at all, but it is something I'd like to fix if I could - I like having the choice.

Second... when starting firefox from the command line, it starts fine, but I now get all sorts of bizarre error/warnings that concern me. There's too many of them for me to even list, but this is a large portion of what scrolls by on screen.

[begin warning/error message]

(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed
(Gecko:19627): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(Gecko:19627): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `gdk_window_is_viewable (src)' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed
(Gecko:19627): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(Gecko:19627): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `gdk_window_is_viewable (src)' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed
(Gecko:19627): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(Gecko:19627): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `gdk_window_is_viewable (src)' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed
(Gecko:19627): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

[end warning/error messages]

Anything I can do here to fix this? What's going on?

---

### Post by katiad on 2006-01-29
Anybody??

---

### Post by katiad on 2006-02-09
No one has a clue?

---

### Post by aysiu on 2006-02-09
Yes. No one has a clue.
When you post and bump your thread twice and no one responds, it's usually because your problem is unique.

---

### Post by Orval on 2006-02-10
I had a similar problem with gnome apps in KDE. At some point Gnome wouldn't start also. The problems were gone when I removed gtk2-engines-gtk-qt. I couldn't figure out how to solve the problems leaving gtk2-engines-gtk-qt installed, though.

---

