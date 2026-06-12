---
title: "crashing avant-window-navigator"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by mega on 2007-10-04
I'm out of ideas, using 

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator


I get random crash's like this one

~$ avant-window-navigator 
Screen is composited.
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/trash.desktop

(awn-applet-activation:6699): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:6699): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:24751): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

(awn-applet-activation:24753): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed

(avant-window-navigator:6697): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(avant-window-navigator:6697): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GtkWidget'
Segmentation fault (core dumped)
megadeth@megadeth-laptop:~$ 
(awn-applet-activation:6701): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(awn-applet-activation:6701): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(awn-applet-activation:6701): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(awn-applet-activation:6701): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(awn-applet-activation:6701): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(awn-applet-activation:6701): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(awn-applet-activation:6701): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(awn-applet-activation:6701): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by Faud on 2007-10-04
Are you running fiesty or gusty and are you running compiz-fusion.

---

### Post by mega on 2007-10-05
gusty, whatever it comes with, compiz-fusion I guess?

---

### Post by mega on 2007-10-15
Still constantly crashing in gusty/compiz

---

### Post by borovy3488 on 2007-10-15
same problem here. anyone know anything

---

### Post by Faud on 2007-10-15
If you go to your AWN manager, which is under system->preferences. What applets do you hvae installed or are you trying to run ?

---

### Post by mega on 2007-10-16
I have...

awn main menu
launcher/taskmanager
trash applet

---

### Post by mega on 2007-10-18
still crashing, sometimes 10 crashes per day

---

### Post by mega on 2007-10-26
still crashing every day, about once an hour

anyone else having this problem?

---

### Post by VON_CAPO on 2007-10-26
If you really like to use AWN, you could consider to install the package located at getdeb.net, it is super stable.

Nor one single crash so far.

But it lacks of some applets, such "Show desktop" and "Trash", my solution to this was to add those to my upper panel.

---

