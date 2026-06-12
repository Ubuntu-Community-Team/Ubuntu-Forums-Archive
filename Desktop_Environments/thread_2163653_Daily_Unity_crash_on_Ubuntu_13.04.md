---
title: "Daily Unity crash on Ubuntu 13.04"
date: 2013-07-19
forum: Desktop Environments
---

### Post by hamoid on 2013-07-19
Hi! :) I think I need some help:

**Symptoms**
My Ubuntu is loosing the window titles and icons once or twice per day. The left bar (Unity?) disappears, the Start key no longer responds, and key presses go automatically to whatever window is under the mouse pointer, not the window on front.
This has been happening I think since I upgraded to Ubuntu 13.04.

**What I tried**
Opening a terminal (CTRL+ALT+T still works) and restarting unity, compiz and lightdm, one by one, but nothing except a full restart fixes the problem.

**When it happens**
The action that causes the problem varies, but it's always something I do. Either pressing the Start key, quickly typing something and then pressing ESC, or the last time it happened was when I double clicked an MP4 video file attached in an Thunderbird e-mail. I chose "open with video player", and then I could hear the audio, but the video was gone, and Unity disappeared. This made me suspect the graphics card is involved in this problem.

**System**
i7 quad core laptop with integrated Intel graphics, 4 years old, ssd with 10 gb free, 4gb ram, /tmp mounted in ram, display port 24" monitor, echo indigo expresscard sound card, up to date Ubuntu 13.04.

**Questions**
1) is there something I can type in the terminal to get back unity without having to restart?
2) in which log file should I look to find out what's going on?

---

### Post by dino99 on 2013-07-19
mostly due to compiz i suppose (not all the plugins are bug free; and some settings cant work together), so reset it:

sudo apt-get install dconf-tools
dconf reset -f /org/compiz/
setsid unity

note: using the daily built means accepting some issues

---

### Post by hamoid on 2013-07-19
I did what you suggested and that triggered the error.

```
myuser@myuser:~/Desktop$ dconf reset -f /org/compiz/
myuser@myuser:~/Desktop$ setsid unity
myuser@myuser:~/Desktop$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2013-07-19 12:55:20 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Autopilot.Introspection' yet as we don't have a connection, waiting for it...
WARN  2013-07-19 12:55:20 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Unity.Debug.Logging' yet as we don't have a connection, waiting for it...
WARN  2013-07-19 12:55:20 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2013-07-19 12:55:20 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2013-07-19 12:55:21 unity.glib.dbus.server GLibDBusServer.cpp:580 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
myuser@myuser:~/Desktop$ WARN  2013-07-19 12:55:21 unity.glib.dbus.proxy GLibDBusProxy.cpp:418 Calling method "CanHibernate" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-07-19 12:55:21 unity.session.gnome GnomeSessionManager.cpp:334 logind CanHibernate call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
WARN  2013-07-19 12:55:21 unity.glib.dbus.proxy GLibDBusProxy.cpp:418 Calling method "CanSuspend" on object path: "/org/freedesktop/login1" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
ERROR 2013-07-19 12:55:21 unity.session.gnome GnomeSessionManager.cpp:334 logind CanSuspend call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.login1 was not provided by any .service files
myuser@myuser:~/Desktop$ intel_do_flush_locked failed: Input/output error

```

To shut down I pressed Ctrl+Alt+F5, typed "sudo shutdown now", but shutdown got stuck , so I had to hold down the power button.

Anything useful in the output above?

---

