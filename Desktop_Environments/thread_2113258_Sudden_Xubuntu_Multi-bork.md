---
title: "Sudden Xubuntu Multi-bork"
date: 2013-02-06
forum: Desktop Environments
---

### Post by llanitedave on 2013-02-06
I logged into a continuing Xubuntu 12.10 session today, and about 1 or two seconds after the desktop appeared, the following happened pretty much simultaneously:

1.  The window titlebars and borders disappeared.
2.  My workspace boxes disappeared one by one -- I had 4, but they closed until there was only one left.
3.  Existing open windows covered up the upper taskbar, with no means to move them away from it.

I was left with no way to move, close, or resize windows.  I used the system preferences from the lower taskbar to put the applications menu there, and from that I used the task manager to kill the open applications that had the dysfunctional windows. However, on re-opening those apps, the windows appeared again in their dysfunctional mode.

In the System Settings, I reset the number of workspaces to 4, however, they did not get recreated in the list box.

Also in System Settings, the Window Manager and Window Manager Tweaks icons did not respond to mouse clicks, so if there's any fix in there I wasn't able to access it.

I haven't seen anything quite like this before, and there doesn't seem to be any thread on the forums that describes the same thing.  I deleted the ~/cache/session folder, with no change.

Anybody have any hints?

---

### Post by LewisTM on 2013-02-07
There are many threads here describing the same thing ):P
A few: [http://ubuntuforums.org/showthread.php?t=1765417](http://ubuntuforums.org/showthread.php?t=1765417)
[http://ubuntuforums.org/showthread.php?t=1999103](http://ubuntuforums.org/showthread.php?t=1999103)
[http://ubuntuforums.org/showthread.php?t=1968485](http://ubuntuforums.org/showthread.php?t=1968485)

The solution:
```
xfwm4 --replace
```
Cheers!

---

### Post by llanitedave on 2013-02-08
Ah, thanks.  That did work.  The reason I couldn't find those threads may be that I couldn't find any other words to describe it but "borked"!

---

### Post by dentaku65 on 2013-02-09
Please post the content of
```
cat ~/.xsession-errors
```

---

### Post by llanitedave on 2013-02-09
> **dentaku65 said:**
> Please post the content of
```
cat ~/.xsession-errors
```

This is the section that references Xfce:  (I'm not sure of the dates on them, since it's now been working properly for a couple of days)

(xfce4-session:1851): Wnck-CRITICAL **: wnck_workspace_activate: assertion `WNCK_IS_WORKSPACE (space)' failed

(polkit-gnome-authentication-agent-1:1943): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:1943): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

(update-notifier:1932): GLib-GIO-CRITICAL **: g_mount_can_eject: assertion `G_IS_MOUNT (mount)' failed

(update-notifier:1932): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(update-notifier:1932): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(update-notifier:1932): GLib-GIO-CRITICAL **: g_mount_can_eject: assertion `G_IS_MOUNT (mount)' failed

(update-notifier:1932): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
xfce4-panel: No window manager registered on screen 0. To start the panel without this check, run with --disable-wm-check.
xfsettingsd: No window manager registered on screen 0.

(xfsettingsd:1892): xfsettingsd-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.
** Message: applet now embedded in the notification area

(xfce4-indicator-plugin:2061): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:2061): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfce4-indicator-plugin:2061): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfce4-indicator-plugin:2061): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

---

