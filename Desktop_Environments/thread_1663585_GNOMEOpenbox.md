---
title: "GNOME/Openbox"
date: 2011-01-09
forum: Desktop Environments
---

### Post by Imaginary on 2011-01-09
I've got a brand new installation of Meerkat from the latest Ubuntu alternate CD.  I'm trying to switch my window manager over to Openbox, but when I log in using the GNOME/Openbox session choice, I keep getting metacity.  If I then open a terminal and run 'openbox --replace &', it works with no problems.

I've been spelunking around through the scripts, and the problem seems to happen when openbox-gnome-session executes gnome-session.  Relevant section of .xsession-errors is:

```

GNOME_KEYRING_CONTROL=/tmp/keyring-VstYT5
SSH_AUTH_SOCK=/tmp/keyring-VstYT5/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-VstYT5
SSH_AUTH_SOCK=/tmp/keyring-VstYT5/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-VstYT5
SSH_AUTH_SOCK=/tmp/keyring-VstYT5/ssh

(polkit-gnome-authentication-agent-1:9282): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:9282): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

** (gnome-settings-daemon:9330): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:9330): WARNING **: Could not acquire name
** Message: applet now removed from the notification area
** (nm-applet:9284): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:9284): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
** (nm-applet:9284): DEBUG: foo_client_state_changed_cb

(nautilus:9289): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0
** Message: applet now embedded in the notification area
Unable to find a synaptics device.
** (nm-applet:9284): DEBUG: foo_client_state_changed_cb
** (update-notifier:9671): DEBUG: aptdaemon on bus: 0
** (update-notifier:9671): DEBUG: Skipping reboot required

(yelp:9743): Gtk-CRITICAL **: IA__gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:9743): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:9743): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:9743): Gtk-CRITICAL **: IA__gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(yelp:9743): Gtk-CRITICAL **: IA__gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:9743): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:9743): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:9743): Gtk-CRITICAL **: IA__gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

```

I tried turning on the --debug flag to gnome-session.  It says it starts openbox first, but then closes it and opens up metacity as a fallback.  Also, for some reason the output seems have have several references to compiz, even though I'm not using it.  'ps -e | grep compiz' confirms it's not running.

Any ideas?

---

### Post by kerry_s on 2011-01-09
just put "openbox --replace" in the startup.

---

### Post by Imaginary on 2011-01-11
Nope, still getting Metacity.  Suprisingly, the call to openbox --replace also didn't make any report to .xsession_errors.  Any more ideas?

---

### Post by Imaginary on 2011-02-13
Final update:

Followed the directions for doing so under ArchLinux at:

[https://wiki.archlinux.org/index.php/Openbox#GNOME_2.24_and_2.26](https://wiki.archlinux.org/index.php/Openbox#GNOME_2.24_and_2.26)

This solved the problem.  I also removed OpenBox from my Startup Applications; the problem remained solved.

---

