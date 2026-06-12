---
title: "xfce4-mixer-plugin is broken"
date: 2009-01-03
forum: Desktop Environments
---

### Post by plutino on 2009-01-03
The volume control applet stops to work since a recent update.  Attached is the error message I dig out of the .xsession-errors file.  I'm using Xubuntu 8.10 on a Thinkpad T61.  Does anyone get the same problem and find a solution?  Thanks.


```
The program 'xfce4-mixer-plugin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 208 error_code 10 request_code 33 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
** Message: Volume Control: screen changed: 0

** Message: No valid plug window.

(xfce4-panel:5750): Gtk-CRITICAL **: gtk_socket_get_id: assertion `GTK_WIDGET_ANCHORED (so
cket)' failed

** (xfce4-panel:5750): CRITICAL **: An item was unexpectedly removed: "Volume Control".

```

---

### Post by amel48 on 2009-01-05
> **plutino said:**
> The volume control applet stops to work since a recent update.  Attached is the error message I dig out of the .xsession-errors file.  I'm using Xubuntu 8.10 on a Thinkpad T61.  Does anyone get the same problem and find a solution?  Thanks.


```
The program 'xfce4-mixer-plugin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 208 error_code 10 request_code 33 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
** Message: Volume Control: screen changed: 0

** Message: No valid plug window.

(xfce4-panel:5750): Gtk-CRITICAL **: gtk_socket_get_id: assertion `GTK_WIDGET_ANCHORED (so
cket)' failed

** (xfce4-panel:5750): CRITICAL **: An item was unexpectedly removed: "Volume Control".

```

This is just a "mee too". Same happens here. You are not alone.

No idea so far ...

---

