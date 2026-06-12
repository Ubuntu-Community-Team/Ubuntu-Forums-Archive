---
title: "Totally screwed up x-session-manager?"
date: 2014-04-12
forum: Desktop Environments
---

### Post by f00dl3 on 2014-04-12
(using Ubuntu 13.10 all latest updates)

So I don't know how I did this. Every time I log into Ubuntu (locally on the physical machine) with my normal user account I am getting a black screen and kicked back to the login screen again. I checked the ~/.xsession-errors and this is what it shows:

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1" 
      after 4176 requests (4176 known processed) with 0 events remaining. 
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":2" 
      after 4133 requests (4133 known processed) with 0 events remaining.


I was playing around with X11VNC and TightVNC today trying to get VNC server working, looking at numerous solutions. Never could get it working properly. I have created a new user account for local access to the desktop via the shell as a work-around and it's working fine.

At one point I read something that had me modify my /etc/X11/xorg.conf file to change the video driver to "vesa" from "nVidia" - luckly I created a backup but that apparently did no good as even after I restored the backup file I am still having this problem.

Is there any way to fix this or is that user account that I played around with VNC server stuff on ruined? I'm guessing the user account home folder ~/.X* files may have become corrupted somehow.

Full log:

Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: gnome-settings-daemon main process (6628) terminated with status 1
init: unity-panel-service main process (6639) terminated with status 1
init: update-notifier-crash (/var/crash/_usr_bin_Xorg.0.crash) main process (29746) terminated with status 1
init: hud main process (6632) killed by TERM signal
init: upstart-dbus-session-bridge main process (6600) terminated with status 1
init: gnome-session main process (6635) terminated with status 1
Xsession: X session started for astump at Sat Apr 12 17:16:59 CDT 2014
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:astump being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
Script for cjkv started at run_im.
Script for default started at run_im.
Script for cjkv started at run_im.
Script for default started at run_im.
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256

** (process:3071): WARNING **: software acceleration check failed: Child process exited with code 1

** (x-session-manager:3071): CRITICAL **: We failed, but the fail whale is dead. Sorry....
Xsession: X session started for root at Sat Apr 12 17:37:01 CDT 2014
localuser:root being added to access control list
Script for cjkv started at run_im.
Script for default started at run_im.
Script for cjkv started at run_im.
Script for default started at run_im.
x-session-manager[2381]: WARNING: Could not parse desktop file gwibber.desktop or it references a not found TryExec binary

** (gnome-keyring-daemon:2446): WARNING **: couldn't create socket directory: Permission denied

** (gnome-keyring-daemon:2446): WARNING **: couldn't bind to control socket: /home/astump/.cache/keyring-0PRaVP/control: No such file or directory
Home directory not accessible: Permission denied
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

** (gnome-keyring-daemon:2455): WARNING **: couldn't create socket directory: Permission denied

** (gnome-keyring-daemon:2455): WARNING **: couldn't bind to control socket: /home/astump/.cache/keyring-f53BXR/control: No such file or directory
x-session-manager[2381]: WARNING: App 'pulseaudio.desktop' exited with code 1

** (gnome-keyring-daemon:2457): WARNING **: couldn't create socket directory: Permission denied

** (gnome-keyring-daemon:2457): WARNING **: couldn't bind to control socket: /home/astump/.cache/keyring-RfIq4R/control: No such file or directory

** (gnome-keyring-daemon:2458): WARNING **: couldn't create socket directory: Permission denied

** (gnome-keyring-daemon:2458): WARNING **: couldn't bind to control socket: /home/astump/.cache/keyring-c8eWDR/control: No such file or directory
Home directory not accessible: Permission denied

(gnome-settings-daemon:2451): Gvc-WARNING **: Failed to connect context: OK
Home directory not accessible: Permission denied
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp

(gnome-settings-daemon:2451): IBUS-WARNING **: The owner of /home/astump/.config/ibus/bus is not root!
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
** Message: applet now removed from the notification area
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/root/.compiz/session/10e354ee4784c26086139734222453231800000023810001"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom

** (nm-applet:2581): WARNING **: Failed to register as an agent: (32) Session not found
** Message: using fallback from indicator to GtkStatusIcon

(nautilus:2578): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed

(nautilus:2578): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed

(nautilus:2578): IBUS-WARNING **: The owner of /home/astump/.config/ibus/bus is not root!
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (core) - Warn: Attempted to restack relative to 0x1c0000c which is not a child of the root window or a window compiz owns

** (gnome-user-share:2671): WARNING **: gnome-user-share cannot be started as root for security reasons.

(zeitgeist-datahub:2679): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(zeitgeist-datahub:2679): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

** (update-notifier:2714): WARNING **: not starting for system user
Xsession: X session started for root at Sat Apr 12 17:41:09 CDT 2014
localuser:root being added to access control list
Script for cjkv started at run_im.
Script for default started at run_im.
Script for cjkv started at run_im.
Script for default started at run_im.
x-session-manager[2812]: WARNING: Could not parse desktop file gwibber.desktop or it references a not found TryExec binary

** (gnome-keyring-daemon:2843): WARNING **: couldn't create socket directory: Permission denied

** (gnome-keyring-daemon:2843): WARNING **: couldn't bind to control socket: /home/astump/.cache/keyring-w2bUKj/control: No such file or directory
Home directory not accessible: Permission denied
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

** (gnome-keyring-daemon:2852): WARNING **: couldn't create socket directory: Permission denied

** (gnome-keyring-daemon:2852): WARNING **: couldn't bind to control socket: /home/astump/.cache/keyring-rEFaLk/control: No such file or directory
x-session-manager[2812]: WARNING: App 'pulseaudio.desktop' exited with code 1

** (gnome-keyring-daemon:2855): WARNING **: couldn't create socket directory: Permission denied

** (gnome-keyring-daemon:2855): WARNING **: couldn't bind to control socket: /home/astump/.cache/keyring-CPEkpk/control: No such file or directory
Home directory not accessible: Permission denied

(gnome-settings-daemon:2849): Gvc-WARNING **: Failed to connect context: OK
Home directory not accessible: Permission denied

(gnome-settings-daemon:2849): IBUS-WARNING **: The owner of /home/astump/.config/ibus/bus is not root!
** Message: couldn't communicate with already running daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (gnome-keyring-daemon:2856): WARNING **: couldn't create socket directory: Permission denied

** (gnome-keyring-daemon:2856): WARNING **: couldn't bind to control socket: /home/astump/.cache/keyring-TTBeFb/control: No such file or directory
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl

** (polkit-gnome-authentication-agent-1:2939): WARNING **: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Cannot register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/root/.compiz/session/1051919ba7ebbde4a139734246996881100000028120001"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
** Message: applet now removed from the notification area

** (nm-applet:2941): WARNING **: Failed to register as an agent: (32) Session not found

(nautilus:2940): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed

(nautilus:2940): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed

(nautilus:2940): IBUS-WARNING **: The owner of /home/astump/.config/ibus/bus is not root!
** Message: using fallback from indicator to GtkStatusIcon
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (core) - Warn: Attempted to restack relative to 0x1400191 which is not a child of the root window or a window compiz owns

** (gnome-user-share:2999): WARNING **: gnome-user-share cannot be started as root for security reasons.

(zeitgeist-datahub:3010): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(zeitgeist-datahub:3010): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

** (update-notifier:3045): WARNING **: not starting for system user

(gnome-screensaver:2678): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-screensaver:2678): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-screensaver:2678): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-screensaver:2678): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-screensaver:2678): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-screensaver:3008): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-screensaver:3008): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-screensaver:3008): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-screensaver:3008): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-screensaver:3008): Gtk-CRITICAL **: gtk_widget_set_visible: assertion 'GTK_IS_WIDGET (widget)' failed

(gnome-settings-daemon:2849): color-plugin-WARNING **: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/cups_Canon_MP620_series

(gnome-settings-daemon:2451): color-plugin-WARNING **: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/cups_Canon_MP620_series
x-session-manager[2381]: Gdk-WARNING: x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

** Message: PID 3536 (we are 2581) sent signal 15, shutting down...
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : Default

compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : Default
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

---

### Post by f00dl3 on 2014-04-13
OK - so it dawned on me - I ran a chmod 755 & chown (user) on ~/.Xauthority and that let me log in. (While I was at it I just chown'd the whole /home/user folder to be safe). I am still getting a "System Problem Detected" at this time, though, it seems minor in comparison. If a reboot doesn't fix that I will post troubleshoot it more tomorrow.

---

### Post by f00dl3 on 2014-04-14
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: update-notifier-crash (/var/crash/_usr_bin_Xorg.0.crash) main process (2265) terminated with status 1



Much cleaner ~/.xsession-errors log!

Still getting the System Problem Detected every time I boot up now. Not sure if I can fix that. May have to check some other logs.

---

### Post by baphomet2 on 2014-04-14
Did you remove everything in /var/crash?  I kept seeing that everytime I booted as well until I removed the crash file and the lock file that was in /var/crash.  Just throwing that out there.  :)

---

