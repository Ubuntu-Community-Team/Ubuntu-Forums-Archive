---
title: "Continual xsession erros; cannot use key apps. 10.10"
date: 2011-04-14
forum: Desktop Environments
---

### Post by XEtedBear on 2011-04-14
For the past week I have been getting continual entries in a hidden log in my home directory called .xsessions-errors. At the same time I find that the most important applications (aside from Firefox and Libre Office) will no longer run - they immediately cause a reset of the X system (KMyMoney, Scribus, Gimp, BeyondCompare, Audacity, Here is this morning's log:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-XhWihS
GNOME_KEYRING_CONTROL=/tmp/keyring-XhWihS
GNOME_KEYRING_CONTROL=/tmp/keyring-XhWihS
SSH_AUTH_SOCK=/tmp/keyring-XhWihS/ssh

(polkit-gnome-authentication-agent-1:1631): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1631): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
Unable to find a synaptics device.
Initializing nautilus-gdu extension
Starting gtk-window-decorator
I/O warning : failed to load external entity "/home/tony/.compiz/session/106b6006c7eae70b63130276368651470900000015480027"

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: applet now embedded in the notification area
/usr/bin/compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:35: GtkWarning: Ignoring the separator setting
  self.builder.add_from_file(path)
** (update-notifier:1809): DEBUG: aptdaemon on bus: 0
** (update-notifier:1809): DEBUG: Skipping reboot required
WARNING:root:timeout reached, exiting
** (update-notifier:1809): DEBUG: --security-updates-unattended: 1


(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1621): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed


```

I guess my first reaction is to reinstall Ubuntu - but this is not the 1 hour job  that it first appears. Backing up and restoring all ones data, downloading and setting up apps again, relearning what customisations I had and so on takes between 2 and 3 days. 

Is there some process I can follow to avoid this huge time cost and that will 'reset' my X system?

---

