---
title: "gnome-settings-daemon disappeared"
date: 2007-04-15
forum: Desktop Environments
---

### Post by Sciamano on 2007-04-15
Hi everyone!
My system crashed unexpectedly when trying to enable DMA on my DVD burner.
The PC restarted, then fsck found some errors. It entered the maintenance shell, where I followed the instructions on screen and launched *fsck*. I then answered "Yes" everytime it found an error and asked if I wanted it to resolve the issue.
The system rebooted again and now...

... in Gnome the desktop theme does not show up anymore, and at startup a popup window shows up saying:

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.
```

If I try to launch almost every applet in the  System->Preferences/Administration menus, another popup shows up saying:

```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

I've also tried to launch *gnome-settings-daemon* in a shell, but this is the result:

```
Warning: Only changing the first 32 of 18 buttons.

(gnome-settings-daemon:6887): GSwitchIt-WARNING **: Unable to connect to dbus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

** (gnome-settings-daemon:6887): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed

** (gnome-settings-daemon:6887): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (gnome-settings-daemon:6887): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

** (bug-buddy:6895): WARNING **: Couldn't load icon for Open Folder

```

I've read on the board to check "ifconfig" to see if lo is up, and it is. 
/etc/hosts and /etc/network/adapters are configured fine.

I've also tried to reinstall Gnome, but with no success.
What else can I do?

I could reinstall the system of course, but how do I do that without losing all the (intensive) configuration I've done to the system during these months I've been using it? I don't want to reinstall everything from scratch...

Thanks,
Luca

---

