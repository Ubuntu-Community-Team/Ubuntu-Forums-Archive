---
title: "Gnome not loading, no desktop loading"
date: 2008-01-10
forum: Desktop Environments
---

### Post by sepuko on 2008-01-10
OK, I've only been installing some Open Office related things and everything worked fine until I rebooted. I logged in, no Gnome, no Compiz, no Emerald, no nothing. So i restarted the x server and went in to gnome failsafe .
gave it sudo gnome-panel and went into "appearance". It gave me an error message that there's been some conflict preventing the Gnome from loading that had to do with KDE Bonobo .
I'm not quite sure what should that mean. I tried reinstalling all of the components of Gnome. Though that would solve it all so I rebooted and went in my user. This time background went black and my mouse remained undecorated, no Gnome, no Compiz, no Emerald again.
(gnome-appearance-properties:10188): GLib-CRITICAL **: g_array_free: assertion `array' failed
This is one of the error messages I continue to get. In the begining there were some error messages in regards to GTK so I though,"oh, I just installed something gtk related for OpenOffice, better remove it", did so, no such error message now.
Unable to open desktop file file:///usr/share/applications/yelp.desktop for pane
this is what I get when I type the sudo gnome-panel
Any help will be appreciated as would any question that would pull additional details out of my head.

---

### Post by sepuko on 2008-01-10
OK. here's some terminal output:
sepuko@POWERSERVER:~$ gnome-settings-daemon

** (gnome-settings-daemon:13243): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-koDRF2avXu: Connection refused

(gnome-settings-daemon:13243): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-BzhfBYtulJ: Connection refused

(gnome-settings-daemon:13243): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object
Warning:          No symbols defined for <SYRQ> (keycode 92)
Warning:          No symbols defined for <II65> (keycode 101)
Warning:          No symbols defined for <BRK> (keycode 114)
Warning:          No symbols defined for <FK13> (keycode 118)
Warning:          No symbols defined for <FK14> (keycode 119)
Warning:          No symbols defined for <FK15> (keycode 120)

Additionally(Appearance run):
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

Anybody, any ideas?

---

