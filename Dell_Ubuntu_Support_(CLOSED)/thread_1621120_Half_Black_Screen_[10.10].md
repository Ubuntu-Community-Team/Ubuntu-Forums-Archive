---
title: "Half Black Screen [10.10]"
date: 2010-11-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EloRampage93 on 2010-11-13
Two days ago, the update manager offered me some updates but when I agreed to install them, it told me that it couldn't install all the updates and that I had to do a partial upgrade, one package what removed, I think it was related to compiz, But i didn't rebooted until today, when my pc rebooted everything seemed fine but when I logged in, the lower half of my screen went black and all the compiz extra settings were removed.

Here's a screenshot: [http://img687.imageshack.us/img687/7491/blackscreen.png]("http://img687.imageshack.us/img687/7491/blackscreen.png")

I have a Dell Inspiron 1525 with an Intel graphics card.

---

### Post by EloRampage93 on 2010-11-13
Trying to do something I wrote on terminal "gtk-window-decorator --replace" and I got this: 


(gtk-window-decorator:2485): Gdk-WARNING **: GdkWindow 0x4e000a6 unexpectedly destroyed

(gtk-window-decorator:2485): Gtk-CRITICAL **: IA__gtk_widget_get_window: assertion `GTK_IS_WIDGET (widget)' failed

(gtk-window-decorator:2485): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkImage'

(gtk-window-decorator:2485): Gtk-CRITICAL **: IA__gtk_image_set_from_pixmap: assertion `GTK_IS_IMAGE (image)' failed

(gtk-window-decorator:2485): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWindow'

(gtk-window-decorator:2485): Gtk-CRITICAL **: IA__gtk_window_resize: assertion `GTK_IS_WINDOW (window)' failed

(gtk-window-decorator:2485): Gdk-CRITICAL **: IA__gdk_window_reparent: assertion `GDK_IS_WINDOW (window)' failed

(gtk-window-decorator:2485): Gdk-CRITICAL **: IA__gdk_window_lower: assertion `GDK_IS_WINDOW (window)' failed

(gtk-window-decorator:2485): Gtk-CRITICAL **: IA__gtk_widget_get_window: assertion `GTK_IS_WIDGET (widget)' failed

(gtk-window-decorator:2485): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkImage'

(gtk-window-decorator:2485): Gtk-CRITICAL **: IA__gtk_image_set_from_pixmap: assertion `GTK_IS_IMAGE (image)' failed

(gtk-window-decorator:2485): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkWindow'

(gtk-window-decorator:2485): Gtk-CRITICAL **: IA__gtk_window_resize: assertion `GTK_IS_WINDOW (window)' failed

(gtk-window-decorator:2485): Gdk-CRITICAL **: IA__gdk_window_reparent: assertion `GDK_IS_WINDOW (window)' failed

(gtk-window-decorator:2485): Gdk-CRITICAL **: IA__gdk_window_lower: assertion `GDK_IS_WINDOW (window)' failed

What does all this errors mean?

In addition I tried to install compiz-fusion-plugins-extra again and I got this error message on terminal:

The following packages have unmet dependencies:
 compiz-fusion-plugins-extra : Depends: compiz-core-abiversion-20091102
E: Broken packages

---

