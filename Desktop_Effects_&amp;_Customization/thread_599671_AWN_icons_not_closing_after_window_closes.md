---
title: "AWN icons not closing after window closes"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by Skip McMahan on 2007-11-01
I am using gutsy and installed AWN from the repo in this thread [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981), my graphics card is a Nvidia geforce fx 5200, not sure what my driver version is but I used envy to install it. I use Compiz-fusion for my compositing manager.

My issue is that whenever I close a window the Icon for the window remains in the AWN dock, no task arrow, window title is listed as "no name" and there are no menu functions for the icon. I have had this issue when I installed from source and have tried reinstalling a couple of times.

This is the output when running AWN in a terminal
> skip@skip-desktop:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/local/lib/awn/applets/taskman.desktop
APPLET : /usr/local/lib/awn/applets/main-menu.desktop
APPLET : /usr/local/lib/awn/applets/filebrowser.desktop
APPLET : /usr/local/lib/awn/applets/stacks.desktop
APPLET : /usr/local/lib/awn/applets/awn-system-monitor.desktop
return

(awn-applet-activation:10181): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:10181): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
APPLET : /usr/local/lib/awn/applets/weather.desktop
APPLET : /usr/local/lib/awn/applets/showdesktop.desktop
APPLET : /usr/local/lib/awn/applets/PySwitcher.desktop
APPLET : /usr/local/lib/awn/applets/quit-applet.desktop
APPLET : /usr/local/lib/awn/applets/trash.desktop
APPLET : /usr/local/lib/awn/applets/awnnotificationdaemon.desktop

(awn-applet-activation:10175): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:10175): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
<gtk.gdk.Pixbuf object at 0x82c0e14 (GdkPixbuf at 0x837a730)>
<gtk.gdk.Pixbuf object at 0x82c0edc (GdkPixbuf at 0x836af60)>



and this is what I get when I open and close a firefox window from AWN, the Icon for the window is still in the bar.

> <gtk.gdk.Pixbuf object at 0x82c0eb4 (GdkPixbuf at 0x836ad58)>
<gtk.gdk.Pixbuf object at 0x82c0edc (GdkPixbuf at 0x837a970)>
<gtk.gdk.Pixbuf object at 0x82c0eb4 (GdkPixbuf at 0x83b52b8)>

** (awn-applet-activation:10175): WARNING **: Error loading icon: Icon 'aria' not present in theme


(awn-applet-activation:10175): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(awn-applet-activation:10175): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(awn-applet-activation:10175): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `src != NULL' failed

(awn-applet-activation:10175): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
<gtk.gdk.Pixbuf object at 0x82c0edc (GdkPixbuf at 0x82e9050)>

(PySwitcher.py:10201): Wnck-CRITICAL **: update_client_list: assertion `reentrancy_guard == 0' failed
<gtk.gdk.Pixbuf object at 0x82c0eb4 (GdkPixbuf at 0x82e90c0)>
<gtk.gdk.Pixbuf object at 0x82c0edc (GdkPixbuf at 0x82e9220)>
<gtk.gdk.Pixbuf object at 0x82c0eb4 (GdkPixbuf at 0x82e9290)>
<gtk.gdk.Pixbuf object at 0x82c0edc (GdkPixbuf at 0x82e9300)>
<gtk.gdk.Pixbuf object at 0x82c0eb4 (GdkPixbuf at 0x82e9370)>
<gtk.gdk.Pixbuf object at 0x82c0edc (GdkPixbuf at 0x82e9400)>




Any help is greatly appreciated,

---

### Post by Skip McMahan on 2007-11-02
OK, I upgraded AWN and now the Icon issue is fixed, but I cannot start awn-manager. Here is the terminal output.

> skip@skip-desktop:~$ awn-manager
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 43, in <module>
    from awnTheme import AwnThemeManager
ImportError: No module named awnTheme
skip@skip-desktop:~$ 


Should I be filing bug reports on this? If so where?

---

### Post by Skip McMahan on 2007-11-02
Fixed everything by removing AWN and awn-extras and recompiling from source.

---

