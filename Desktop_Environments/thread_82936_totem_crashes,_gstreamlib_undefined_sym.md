---
title: "totem crashes, gstreamlib undefined sym"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Michael Matthews on 2005-10-27
5.10 new install
$ totem

(totem:9584): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:9584): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
totem: symbol lookup error: /usr/lib/gstreamer-0.8/libgstgoom.so: undefined symbol: gst_adapter_new
[email]mjmatt@mjmatt01:~/.gcon[/email]f/apps$ dpkg -l | grep totem
ii  libtotem-plparser0                    1.2.0-0ubuntu3                     Totem Playlist Parser library - runtime vers
ii  totem                                 1.2.0-0ubuntu3                     A simple media player for the Gnome desktop
ii  totem-gstreamer                       1.2.0-0ubuntu3                     A simple media player for the Gnome desktop

Is there a fix for this?

---

