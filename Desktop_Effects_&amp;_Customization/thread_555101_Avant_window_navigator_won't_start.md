---
title: "Avant window navigator won't start"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by medeshago on 2007-09-19
```
medeshago@nosotros:~$ avant-window-navigator Screen is composited.
APPLET : /usr/lib/awn/applets/stack.desktop

** (avant-window-navigator:8919): CRITICAL **: spotlight_init: assertion `error == NULL' failed
LOADED : /usr/share/applications/firefox.desktop

** (avant-window-navigator:8919): CRITICAL **: spotlight_init: assertion `error == NULL' failed
LOADED : /usr/share/applications/gnome-terminal.desktop

** (avant-window-navigator:8919): CRITICAL **: spotlight_init: assertion `error == NULL' failed
LOADED : /usr/share/applications/evolution-mail.desktop

** (avant-window-navigator:8919): CRITICAL **: spotlight_init: assertion `error == NULL' failed
LOADED : /usr/share/applications/kde/amarok.desktop

** (avant-window-navigator:8919): CRITICAL **: spotlight_init: assertion `error == NULL' failed
LOADED : /home/medeshago/.local/share/applications/pidgin.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop

(avant-window-navigator:8919): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(avant-window-navigator:8919): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(avant-window-navigator:8919): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(avant-window-navigator:8919): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

(avant-window-navigator:8919): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(avant-window-navigator:8919): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed
Fallo de segmentación (core dumped)
medeshago@nosotros:~$ 
(awn-applet-activation:8921): Gdk-WARNING **: GdkWindow 0x380001d unexpectedly destroyed

(awn-applet-activation:8921): Gdk-WARNING **: GdkWindow 0x3800004 unexpectedly destroyed
The program 'awn-applet-activation' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 165 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```



I already tried to reinstall it.

---

### Post by hyperair on 2007-09-20
Where did you install Avant Window Navigator from? And what version?

---

