---
title: "Remmina 1.4.33 crashes on high resolution monitors"
date: 2023-12-20
forum: Desktop Environments
---

### Post by ericnux on 2023-12-20
Hi.

I'm using Ubuntu 23.10 and remmina 1.4.33 installed using snap.
When opening an RDP-connection remmina simply craches. This output is from the debug console
```
(org.remmina.Remmina:9135): Gtk-WARNING **: 12:48:59.915: infinite surface size not supported
(org.remmina.Remmina:9135): Gtk-WARNING **: 12:48:59.915: drawing failure for widget 'GtkImage': invalid value (typically too big) for the size of the input (surface, pattern, etc.)
(org.remmina.Remmina:9135): Gtk-WARNING **: 12:48:59.915: drawing failure for widget 'GtkToggleButton': invalid value (typically too big) for the size of the input (surface, pattern, etc.)
(org.remmina.Remmina:9135): Gtk-WARNING **: 12:48:59.915: drawing failure for widget 'GtkToggleToolButton': invalid value (typically too big) for the size of the input (surface, pattern, etc.)
(org.remmina.Remmina:9135): Gtk-WARNING **: 12:48:59.915: drawing failure for widget 'GtkToolbar': invalid value (typically too big) for the size of the input (surface, pattern, etc.)
(org.remmina.Remmina:9135): Gtk-WARNING **: 12:48:59.915: drawing failure for widget 'GtkGrid': invalid value (typically too big) for the size of the input (surface, pattern, etc.)
(org.remmina.Remmina:9135): Gtk-WARNING **: 12:48:59.915: drawing failure for widget 'RemminaConnectionWindow': invalid value (typically too big) for the size of the input (surface, pattern, etc.)
(org.remmina.Remmina:9135): Gdk-ERROR **: 12:48:59.946: The program 'org.remmina.Remmina' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue'.
  (Details: serial 11591 error_code 2 request_code 53 (core protocol) minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)
```

I'm running the standard Gnome shell.

---

