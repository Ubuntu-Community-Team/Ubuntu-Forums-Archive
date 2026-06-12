---
title: "Ubuntu 20.04 Desktop unusable after running updates"
date: 2021-01-12
forum: Desktop Environments
---

### Post by keep-tryin on 2021-01-12
I ran updates for my Ubuntu 20.04 machine  last night. This morning I can logon and it shows my desktop put it will not open any application it either freezes or returns to the logon screen. I accessed via ssh from another computer and tried 
 ```
sudo apt-get install --reinstall ubuntu-desktop
```
hoping it would solve the problem but still have the same problem but it did not 
Here are some of what is in the syslog don't know if any of it is helpful

```
Jan 12 08:54:27 star gnome-shell[4510]: Failed to create file /run/user/1000/gnome-shell-disable-extensions: Error opening file &#8220;/run/user/1000/gnome-shell-disable-extensions&#8221;: File exists
Jan 12 08:54:27 star dbus-daemon[362]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jan 12 08:54:27 star systemd[1]: Started PackageKit Daemon.
Jan 12 08:54:27 star dbus-daemon[4158]: [session uid=1000 pid=4158] Activating service name='org.freedesktop.FileManager1' requested by ':1.27' (uid=1000 pid=4510 comm="/usr/bin/gnome-shell " label="unconfined")
Jan 12 08:54:28 star dbus-daemon[362]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.285' (uid=1000 pid=4510 comm="/usr/bin/gnome-shell " label="unconfined")
Jan 12 08:54:28 star systemd[1]: Starting Hostname Service...
Jan 12 08:54:28 star dbus-daemon[4158]: [session uid=1000 pid=4158] Activating service name='org.gnome.Shell.Notifications' requested by ':1.27' (uid=1000 pid=4510 comm="/usr/bin/gnome-shell " label="unconfined")
Jan 12 08:54:28 star systemd[1165]: Started GNOME Shell on X11.
Jan 12 08:54:28 star systemd[1165]: Reached target GNOME Color management.
Jan 12 08:54:28 star gnome-shell[3988]: Failed to set CRTC gamma: drmModeCrtcSetGamma on CRTC 45 failed: Permission denied
Jan 12 08:54:28 star gnome-shell[3988]: Failed to set CRTC gamma: drmModeCrtcSetGamma on CRTC 45 failed: Permission denied
Jan 12 08:54:28 star systemd[1165]: Started GNOME Printer notifications.
Jan 12 08:54:28 star systemd[1165]: Reached target GNOME Printer notifications.
Jan 12 08:54:28 star dbus-daemon[362]: [system] Successfully activated service 'org.freedesktop.locale1'
Jan 12 08:54:28 star systemd[1]: Started Locale Service.
Jan 12 08:54:28 star gnome-shell[4510]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
Jan 12 08:54:29 star gsd-media-keys[4680]: Failed to grab accelerator for keybinding settings:hibernate
Jan 12 08:54:29 star gsd-media-keys[4680]: Failed to grab accelerator for keybinding settings:rfkill
Jan 12 08:54:29 star gsd-media-keys[4680]: Failed to grab accelerator for keybinding settings:playback-random
Jan 12 08:54:29 star gsd-media-keys[4680]: Failed to grab accelerator for keybinding settings:playback-repeat
Jan 12 08:54:29 star systemd[1165]: Started GNOME XSettings.
Jan 12 08:54:29 star systemd[1165]: Reached target GNOME XSettings.
Jan 12 08:54:29 star systemd[1165]: Reached target GNOME Session.
Jan 12 08:54:29 star systemd[1165]: Reached target GNOME X11 Session (session: ubuntu).
Jan 12 08:54:29 star systemd[1165]: Reached target Current graphical user session.
Jan 12 08:54:29 star systemd[1165]: Condition check resulted in GNOME Initial Setup being skipped.
Jan 12 08:54:29 star systemd[1165]: Condition check resulted in GNOME Welcome Tour being skipped.
Jan 12 08:54:29 star colord[433]: failed to get session [pid 4675]: No data available
Jan 12 08:54:29 star gnome-shell[3988]: Failed to set CRTC gamma: drmModeCrtcSetGamma on CRTC 45 failed: Permission denied
Jan 12 08:54:29 star org.kde.kdeconnect.daemon.desktop[4754]: kdeconnect.core: Daemon starting
Jan 12 08:54:29 star org.kde.kdeconnect.daemon.desktop[4754]: kdeconnect.core: LanLinkProvider started
Jan 12 08:54:29 star org.kde.kdeconnect.daemon.desktop[4754]: kdeconnect.core: Daemon started
Jan 12 08:54:29 star org.kde.kdeconnect.daemon.desktop[4754]: kdeconnect.core: Broadcasting identity packet
Jan 12 08:54:30 star gnome-shell[4510]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
Jan 12 08:54:30 star gnome-shell[4510]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
Jan 12 08:54:30 star gnome-shell[4510]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
Jan 12 08:54:30 star gnome-shell[4510]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
Jan 12 08:54:30 star gnome-shell[4510]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).Jan 12 08:54:30 star gnome-shell[4510]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
Jan 12 08:54:30 star gnome-shell[4510]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
Jan 12 08:54:30 star gnome-shell[4510]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
Jan 12 08:54:30 star gnome-shell[4510]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
Jan 12 08:54:30 star dbus-daemon[4158]: [session uid=1000 pid=4158] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.27' (uid=1000 pid=4510 comm="/usr/bin/gnome-shell " label="unconfined")
Jan 12 08:54:30 star systemd[1165]: Starting Virtual filesystem metadata service...
Jan 12 08:54:30 star dbus-daemon[4158]: [session uid=1000 pid=4158] Successfully activated service 'org.gtk.vfs.Metadata'
Jan 12 08:54:30 star systemd[1165]: Started Virtual filesystem metadata service.
Jan 12 08:54:30 star gnome-shell[4510]: GNOME Shell started at Tue Jan 12 2021 08:54:27 GMT-0600 (CST)
Jan 12 08:54:30 star gnome-shell[4510]: Registering session with GDM
Jan 12 08:54:30 star /usr/lib/gdm3/gdm-wayland-session[3923]: dbus-daemon[3923]: [session uid=125 pid=3923] Activating service name='org.freedesktop.systemd1' requested by ':1.11' (uid=125 pid=4173 comm="/usr/libexec/gsd-sharing " label="unconfined")
Jan 12 08:54:30 star ibus-daemon[4285]: GChildWatchSource: Exit status of a child process was requested but ECHILD was received by waitpid(). See the documentation of g_child_watch_source_new() for possible causes.
Jan 12 08:54:30 star ibus-daemon[4285]: GChildWatchSource: Exit status of a child process was requested but ECHILD was received by waitpid(). See the documentation of g_child_watch_source_new() for possible causes.
Jan 12 08:54:30 star gsd-color[4675]: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/xrandr_Ancor_Communications_Inc_VX238_H6LMRS049805_gdm_125
Jan 12 08:54:30 star systemd[3901]: pulseaudio.service: Succeeded.
Jan 12 08:54:30 star systemd[1]: session-c4.scope: Succeeded.
Jan 12 08:54:30 star gdm3: Child process -3916 was already dead.Jan 12 08:54:37 star systemd[1165]: Starting GNOME Terminal Server...
Jan 12 08:54:37 star dbus-daemon[4158]: [session uid=1000 pid=4158] Successfully activated service 'org.gnome.Terminal'
Jan 12 08:54:37 star systemd[1165]: Started GNOME Terminal Server.
Jan 12 08:54:37 star systemd[1165]: Started VTE child process 4886 launched by gnome-terminal-server process 4878.
Jan 12 08:54:40 star systemd[1]: Stopping User Manager for UID 125...
Jan 12 08:54:40 star systemd[3901]: Stopped target Main User Target.
Jan 12 08:54:40 star gvfsd[3925]: A connection to the bus can't be made
Jan 12 08:54:40 star tracker-miner-f[3915]: Error while sending AddMatch() message: The connection is closed
Jan 12 08:54:40 star tracker-miner-fs[3915]: Received signal:15->'Terminated'
Jan 12 08:54:40 star tracker-miner-f[3915]: Error while sending AddMatch() message: The connection is closed
Jan 12 08:54:40 star tracker-miner-f[3915]: Error while sending AddMatch() message: The connection is closed
Jan 12 08:54:40 star systemd[1165]: run-user-125-gvfs.mount: Succeeded.
Jan 12 08:54:40 star systemd[3901]: Stopping D-Bus User Message Bus...
also tons of different modset lines with various values like the following
Jan 12 08:54:56 star /usr/lib/gdm3/gdm-x-session[4377]: (II) modeset(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)

```
Any idea how I can get my desktop back to running?

Thank you so much

---

### Post by grahammechanical on 2021-01-12
From the Grub boot menu select Advanced Options for Ubuntu and select an older kernel. The first one on the list might be causing the problem so select a kernel lower down the list and see what happens

Regards

---

### Post by keep-tryin on 2021-01-12
Selecting an older kernel does solve the problem. I had tried to switch to lightdm thinking it might solve the problem. I guess I can switch back to gdm3 and need to find instructions to revert back to the older kernel version for now

---

