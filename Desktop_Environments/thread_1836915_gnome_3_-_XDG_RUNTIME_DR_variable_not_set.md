---
title: "gnome 3 - XDG_RUNTIME_DR variable not set"
date: 2011-08-31
forum: Desktop Environments
---

### Post by morissette on 2011-08-31
mori@freedom:~$ gnome-shell --replace

(gnome-shell:4151): GLib-WARNING **: XDG_RUNTIME_DIR variable not set.  Falling back to XDG cache dir.
Window manager warning: Log level 16: Another compositing manager is running on screen 0
Window manager warning: Log level 8: add_win: assertion `info != NULL' failed
Window manager warning: Log level 8: meta_compositor_sync_window_geometry: assertion `info' failed
Window manager warning: Log level 8: add_win: assertion `info != NULL' failed
Segmentation fault

Any ideas?

---

### Post by skibler on 2011-09-02
The XDG_RUNTIME_DR warning is harmless.

I think it is that second line that is your problem. Have you tried logging in with the GNOME session (instead of the Unity or Ubuntu session)? That should start up gnome3 with gnome-shell, assuming all is installed well.

---

