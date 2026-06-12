---
title: "xsession-errors!  What's wrong?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by &amp;)ky#)^ on 2006-06-10
I'm getting these errors on boot in my home folder as .xsession-errors.
What's wrong?

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jsherby"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/montauk:/tmp/.ICE-unix/6488
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (gnome-cups-icon:6578): WARNING **: IPP request failed with status 1280

** (gnome-cups-icon:6578): WARNING **: IPP request failed with status 1280

(gnome-panel:6555): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:6555): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24

```

---

