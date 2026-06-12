---
title: "Gnome search tool does not open containing folder"
date: 2016-11-07
forum: Desktop Environments
---

### Post by VanillaMozilla on 2016-11-07
Open containing folder is an option in the Gnome-search-tool context menu.  If you select that option, a notice "Opening <file>" appears briefly in the system tray and then disappears.

Here the terminal output.
(nautilus:5786): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:5786): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:5786): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:5786): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:5786): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed


Does anyone have current information on this?  (There is a Gnome bug report on this [671317], but it's from from 2012.)  It would be awfully nice if Ubuntu could finally get a fully functioning search tool.

---

### Post by mc4man on 2016-11-07
Maybe mention what release & session you are using. That has worked fine here in recent history, 14.04 > 16.04, ubuntu session.
Also not sure what "system tray" has to do with this (- Ubuntu doesn't use a systray anymore, maybe some other sessions do.

---

### Post by VanillaMozilla on 2016-11-08
Oh, sorry.  Ubuntu 16.04 Flashback (Metacity).  And I don't know what it's called, but the default panel at the bottom displays running applications, among other things.  That's what I was referring to as the system tray.

And of course the search tool works in Unity, so this problem refers to Flashback.
**EDIT:  Not exactly right.  The search bar in Nautilus works in either desktop.  Gnome-search-tool does not.**  So we're back to the first question.  What's wrong with gnome-search-tool?

---

### Post by VanillaMozilla on 2016-11-12
Bumping this to call attention to the editing that I just did.  The gnome-search-tool has options that the search bar in Nautilus does not, but it's not working right.

---

### Post by VanillaMozilla on 2016-11-13
Someone has recently reported this as bug 1633953.
[https://bugs.launchpad.net/ubuntu/+source/gnome-search-tool/+bug/1633953](https://bugs.launchpad.net/ubuntu/+source/gnome-search-tool/+bug/1633953)

---

