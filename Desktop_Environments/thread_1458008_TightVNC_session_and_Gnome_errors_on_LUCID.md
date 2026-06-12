---
title: "TightVNC session and Gnome errors on LUCID"
date: 2010-04-19
forum: Desktop Environments
---

### Post by ma$$ter on 2010-04-19
hi
please help me understand what is generating the following errors listed in TightVNC logs:

```
19/04/10 18:25:20 Xvnc version TightVNC-1.3.9
19/04/10 18:25:20 Copyright (C) 2000-2007 TightVNC Group
19/04/10 18:25:20 Copyright (C) 1999 AT&T Laboratories Cambridge
19/04/10 18:25:20 All Rights Reserved.
19/04/10 18:25:20 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
19/04/10 18:25:20 Desktop name 'X' (coanda:1)
19/04/10 18:25:20 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
19/04/10 18:25:20 Listening for VNC connections on TCP port 5901
[B][COLOR="Red"]Xlib:  extension "RANDR" missing on display ":1.0".
gnome-session[2126]: WARNING: GSIdleMonitor: IDLETIME counter not found
gnome-session[2126]: WARNING: Unable to determine session: Unable to find session for cookie[/COLOR][/B]
Xlib:  extension "RANDR" missing on display ":1.0".

** (gnome-settings-daemon:2138): WARNING **: Unable to start xrandr manager: RANDR extension is not present
GNOME_KEYRING_CONTROL=/tmp/keyring-HTphjb
GNOME_KEYRING_PID=2140
GNOME_KEYRING_CONTROL=/tmp/keyring-HTphjb
SSH_AUTH_SOCK=/tmp/keyring-HTphjb/ssh

[B][COLOR="#ff0000"]** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...
[/COLOR][/B]Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".
Window manager warning: Log level 32: could not find XKB extension.
Xlib:  extension "RANDR" missing on display ":1.0".

**[COLOR="#ff0000"](polkit-gnome-authentication-agent-1:2164): polkit-gnome-1-WARNING **: Unable to determine the session we are in: Remote Exception invoking org.freedesktop.ConsoleKit.Manager.GetSessionForUnixProcess() on /org/freedesktop/ConsoleKit/Manager at name org.freedesktop.ConsoleKit: org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to find session for cookie org.freedesktop.ConsoleKit.Manager.GeneralError Unable%20to%20find%20session%20for%20cookie[/COLOR]**
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "RANDR" missing on display ":1.0".

**[COLOR="#ff0000"](gnome-terminal:2162): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed[/COLOR]**
Xlib:  extension "RANDR" missing on display ":1.0".

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...
Initializing nautilus-gdu extension
[B][COLOR="#ff0000"]gnome-session[2126]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.UPower was not provided by any .service files
gnome-session[2126]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.UPower was not provided by any .service files
gnome-session[2126]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.UPower was not provided by any .service files
connect: No route to host[/COLOR][/B]

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...
Xlib:  extension "RANDR" missing on display ":1.0".

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...
connect: Connection timed out

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...
connect: Connection timed out

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...
[B][COLOR="#ff0000"][add-indicator-applet.py] INFO: started
[add-indicator-applet.py] INFO: no indicator applet binary installed, exiting[/COLOR][/B]
Xlib:  extension "RANDR" missing on display ":1.0".
** (update-notifier:2281): DEBUG: Skipping reboot required

[B][COLOR="#ff0000"]** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:2138): WARNING **: Connection failed, reconnecting...[/COLOR][/B]


```The log file keeps growing fast by repeating last line...

---

