---
title: "panel plugins' bug?"
date: 2008-07-07
forum: Desktop Environments
---

### Post by belarus.europe on 2008-07-07
have a problem with some panel plugins in xubuntu 8.04. they disappear from the panel right after i drag them on it. so, "sound" plugin cannot be put neither on horizontal panel nor on vertical. some others like "network load monitor" cannot be put on horizontal panels only. i can put them on vertical one, but after changing orientation of the panle to horizontal the disappear. in a xsession log file after these manipulations i can see lines containing information about possible gtk bug.

any ideas how to make xfce panels work well?

---

### Post by belarus.europe on 2008-07-08
that problem concerns "system load monitor", "CPU graph", "Mount devices" too. error messages can be read in ~/.xsession-errors

---

### Post by belarus.europe on 2008-07-08
if that can help, these are logs from ~/.xsession-errors, which appears after trying to add "volume control" to the panel:

(xfce4-panel:5942): Gtk-CRITICAL **: gtk_socket_get_id: assertion `GTK_WIDGET_ANCHORED (socket)' fa$

** (xfce4-panel:5942): CRITICAL **: An item was unexpectedly removed: "Volume Control".

---

