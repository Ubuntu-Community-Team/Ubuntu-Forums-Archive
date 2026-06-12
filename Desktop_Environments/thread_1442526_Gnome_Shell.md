---
title: "Gnome Shell"
date: 2010-03-30
forum: Desktop Environments
---

### Post by dr.pepper23 on 2010-03-30
I'm having some trouble getting gnome shell to work. I would appreciate any help. Here is the message I get when I  try to run ./gnome-shell --replace

```
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
Panel leaving: a new panel shell is starting.
Window manager warning: Log level 6: GNOME Shell GConf schemas not found.
This generally indicates a building or packaging problem.
Shell killed with signal 6
** (gnome-panel:26000): DEBUG: Removing applet 11.
** (gnome-panel:26000): DEBUG: Removing applet 10.
** (gnome-panel:26000): DEBUG: Removing applet 9.
** (gnome-panel:26000): DEBUG: Removing applet 8.
** (gnome-panel:26000): DEBUG: Removing applet 7.
** (gnome-panel:26000): DEBUG: Removing applet 6.

(gnome-panel:26000): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(gnome-panel:26000): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:26000): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gnome-panel:26000): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(gnome-panel:26000): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-panel:26000): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:26000): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:26000): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-panel:26000): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
** (gnome-panel:26000): DEBUG: Removing applet 5.
** (gnome-panel:26000): DEBUG: Removing applet 4.
cody@cody-laptop:~/gnome-shell/source/gnome-shell/src$ ** (gnome-panel:26000): DEBUG: Removing applet 3.
** (gnome-panel:26000): DEBUG: Removing applet 2.
** (gnome-panel:26000): DEBUG: Removing applet 1.
** (gnome-panel:26000): DEBUG: Removing applet 0.
** (gnome-panel:26035): DEBUG: Adding applet 0.
** (gnome-panel:26035): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:26035): DEBUG: Adding applet 1.
** (gnome-panel:26035): DEBUG: Adding applet 2.
** (gnome-panel:26035): DEBUG: Adding applet 3.
** (gnome-panel:26035): DEBUG: Adding applet 4.
** (gnome-panel:26035): DEBUG: Adding applet 5.
** (gnome-panel:26035): DEBUG: Adding applet 6.
** (gnome-panel:26035): DEBUG: Adding applet 7.
** (gnome-panel:26035): DEBUG: Adding applet 8.
** (gnome-panel:26035): DEBUG: Adding applet 9.
** (gnome-panel:26035): DEBUG: Adding applet 10.
** (gnome-panel:26035): DEBUG: Adding applet 11.
```

---

### Post by psusi on 2010-03-30
Sounds like you decided to go get the source and build it yourself, and are trying to run it without installing it.  Why don't you just install the package from the repositories?  If you do it yourself you will want to run make install to install it, rather than try to run it uninstalled.

---

### Post by dr.pepper23 on 2010-03-30
Ok I installed it from the repositories. But when I run gnome-shell --replace I get this:

```
cody@cody-laptop:~$ gnome-shell --replace &
[1] 13415
cody@cody-laptop:~$ Window manager warning: Failed to read saved session file /home/cody/.config/mutter/sessions/10366ef861d4157fda126996668650949400000015280001.ms: Failed to open file '/home/cody/.config/mutter/sessions/10366ef861d4157fda126996668650949400000015280001.ms': No such file or directory
      JS LOG: conforming method: IntrospectRemote for org.freedesktop.DBus.Introspectable
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
cody@cody-laptop:~$ 

```Is this a problem?

---

### Post by dusdus on 2010-03-31
> **dr.pepper23 said:**
> Ok I installed it from the repositories. But when I run gnome-shell --replace I get this:

```
cody@cody-laptop:~$ gnome-shell --replace &
[1] 13415
cody@cody-laptop:~$ Window manager warning: Failed to read saved session file /home/cody/.config/mutter/sessions/10366ef861d4157fda126996668650949400000015280001.ms: Failed to open file '/home/cody/.config/mutter/sessions/10366ef861d4157fda126996668650949400000015280001.ms': No such file or directory
      JS LOG: conforming method: IntrospectRemote for org.freedesktop.DBus.Introspectable
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
cody@cody-laptop:~$ 

```Is this a problem?

ehm I think I got that message too, but gome shell worked fine.

---

### Post by psusi on 2010-03-31
Sounds like you don't have working 3d acceleration?

---

### Post by dr.pepper23 on 2010-03-31
Anybody know if there is a way to fix that? It seems like gnome-shell only registers my cursor on every other horizontal line. Whenever I open the Activities window I sometimes can't click a button, but if I move the cursor up just slightly it works. I also can't click on the bar at the top when the activities window is open.

---

