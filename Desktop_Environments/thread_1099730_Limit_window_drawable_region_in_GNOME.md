---
title: "Limit window drawable region in GNOME"
date: 2009-03-18
forum: Desktop Environments
---

### Post by C-- on 2009-03-18
I want to limit the region where metacity draws windows. For example, no window can be dragged into the region comprised of the first 100 pixels of the screen's Y axis, and when windows are maximized they are maximized against this boundary instead of the top of the screen. This is similar to the GNOME Panel's functionality. Does anyone know how to do this?

---

### Post by Badmaster on 2009-05-01
looking for this as well!
thanks in advance

---

### Post by C-- on 2009-05-19
> **Badmaster said:**
> looking for this as well!
thanks in advance

I found out the answer: you need to make straight X server calls to set window struts and to set the window type hint to "dock"

The properties are:

_NET_WM_STRUT
_NET_WM_STRUT_PARTIAL
_NET_WM_WINDOW_TYPE

For the window type you use:
_NET_WM_WINDOW_TYPE_DOCK

See here: [COLOR="Blue"][http://standards.freedesktop.org/wm-spec/1.3/ar01s05.html](http://standards.freedesktop.org/wm-spec/1.3/ar01s05.html)[/COLOR]

You initialize property specifiers as Atoms with the XInternAtom function: [COLOR="Blue"][http://tronche.com/gui/x/xlib/window-information/XInternAtom.html](http://tronche.com/gui/x/xlib/window-information/XInternAtom.html)[/COLOR]

You set window properties with XChangeProperty: [COLOR="Blue"][http://tronche.com/gui/x/xlib/window-information/XChangeProperty.html](http://tronche.com/gui/x/xlib/window-information/XChangeProperty.html)[/COLOR]

In Gtk+ if you have a GtkWindow named my_gtk_window, get its GdkWindow:

GdkWindow* my_gdk_window = my_gtk_window->window

Get the X display with GDK_WINDOW_XDISPLAY(my_gdk_window) and the X window with GDK_WINDOW_XWINDOW(my_gdk_window).

---

