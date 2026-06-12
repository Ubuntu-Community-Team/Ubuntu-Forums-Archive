---
title: "Unity can't be reset through terminal- now what?"
date: 2012-05-11
forum: Desktop Environments
---

### Post by several ingredients on 2012-05-11
I was using Compiz to edit Unity, when the program froze up, as did the system clock. I was forced to hard reboot.

It isn't a surprise, then, that unity didn't work after that. I got a blank desktop with only the ability to browse files. I used ctrl+alt+T to access Terminal and try to reset unity, it didn't work. In fact, I used it to get up Firefox to help me find some other commands, but soon after everything went buggy and I couldn't type in firefox, only click. Thankfully, I managed to copy all of the Terminal error messages into Gmail and get that saved before I rebooted. I can boot into GNOME, KDE, Unity (2D) and the recovery console.

Here's the terminal output:
```
paul@paul-Aspire-5738:~$ sudo unity --reset
WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
compiz (core) - Warn: no exact match for ConfigureNotify on 0x1200092!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0x8efff50
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 1366
compiz (core) - Warn: height: 768
compiz (core) - Warn: above: 0
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
paul@paul-Aspire-5738:~$
(compiz:2809): GConf-WARNING **: Got Disconnected from DBus.


(compiz:2809): GConf-WARNING **: The connection to DBus was broken. Can't reinitialize it.

(compiz:2809): GConf-WARNING **: The connection to DBus was broken. Can't reinitialize it.

(compiz:2809): GConf-WARNING **: The connection to DBus was broken. Can't reinitialize it.

(compiz:2809): GConf-WARNING **: The connection to DBus was broken. Can't reinitialize it.

(compiz:2809): GConf-WARNING **: The connection to DBus was broken. Can't reinitialize it.
process 2809: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file ../../dbus/dbus-message.c line 1200.
This is normally a bug in some application using the D-Bus library.
process 2809: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file ../../dbus/dbus-connection.c line 3483.
This is normally a bug in some application using the D-Bus library.
process 2809: arguments to dbus_message_unref() were incorrect, assertion "message != NULL" failed in file ../../dbus/dbus-message.c line 1554.
This is normally a bug in some application using the D-Bus library.
GConf Error: Failed: Unknown error
paul@paul-Aspire-5738:~$
```

---

### Post by wilee-nilee on 2012-05-12
Don't run it in sudo, hit alt-f2 then put in unity --reset

Here is a compiz reset.

[http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html)

You can install the fusion icon and make a launcher in a dock, or on the desktop for the icon, it will restart compiz.

[http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)

---

### Post by several ingredients on 2012-05-14
> **wilee-nilee said:**
> Don't run it in sudo, hit alt-f2 then put in unity --reset

Here is a compiz reset.

[http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html](http://www.ubuntugeek.com/ubuntu-tip-how-to-reset-compiz-settings-to-default-system-settings-from-command-line.html)

You can install the fusion icon and make a launcher in a dock, or on the desktop for the icon, it will restart compiz.

[http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)
I ran unity-- reset without sudo before, then with sudo when it didn't work. I get a somewhat different error from just "unity --reset"
```
paul@paul-Aspire-5738:~$ unity --reset
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done

```At that point, the terminal hangs, attempting to close the process results in a warning that it hasn't yet been completed. Resetting compiz seems to work, but that doesn't resurrect unity.
Below is the verbose output of unity, if it's of any help.
```
unity -v
unity-panel-service: no process found
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libccp.so : No such file or directory
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libbailer.so : No such file or directory
Initializing bailer options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libdetection.so : No such file or directory
Initializing detection options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libcomposite.so : No such file or directory
Initializing composite options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libopengl.so : No such file or directory
Initializing opengl options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libdecor.so : No such file or directory
Initializing decor options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libmousepoll.so : No such file or directory
Initializing mousepoll options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libvpswitch.so : No such file or directory
Initializing vpswitch options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libregex.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libanimation.so : No such file or directory
Initializing animation options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libsnap.so : No such file or directory
Initializing snap options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libexpo.so : No such file or directory
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libmove.so : No such file or directory
Initializing move options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libcompiztoolbox.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libplace.so : No such file or directory
Initializing place options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libgrid.so : No such file or directory
Initializing grid options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libimgpng.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libgnomecompat.so : No such file or directory
Initializing gnomecompat options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libwall.so : No such file or directory
Initializing wall options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libezoom.so : No such file or directory
Initializing ezoom options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libworkarounds.so : No such file or directory
Initializing workarounds options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libstaticswitcher.so : No such file or directory
Initializing staticswitcher options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libresize.so : No such file or directory
Initializing resize options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libfade.so : No such file or directory
Initializing fade options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libscale.so : No such file or directory
Initializing scale options...done
compiz (core) - Debug: Could not stat() file /home/paul/.compiz-1/plugins/libsession.so : No such file or directory
Initializing session options...done
compiz (core) - Debug: refusing to manage window 0x2e00092
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 2710
compiz (core) - Debug: - event window 0x2e00128
compiz (core) - Debug: - x: 0 y: -29 width: 719 height: 407 border: 32, sibling: 0x0
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 2735
compiz (core) - Debug: - event window 0x2e00128
compiz (core) - Debug: - x: 0 y: 0 width: 719 height: 407 border: 8081396, sibling: 0x7b4ff4
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 2756
compiz (core) - Debug: - event window 0x2e00128
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 134731299, sibling: 0x2e00092
compiz (core) - Debug: refusing to manage window 0x2e00128
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 2710
compiz (core) - Debug: - event window 0x2e00128
compiz (core) - Debug: - x: 0 y: -29 width: 719 height: 407 border: 32, sibling: 0x0
compiz (core) - Debug: refusing to manage window 0x2e0012a
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 2735
compiz (core) - Debug: - event window 0x2e00128
compiz (core) - Debug: - x: 0 y: 0 width: 719 height: 407 border: 8081396, sibling: 0x7b4ff4
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 2756
compiz (core) - Debug: - event window 0x2e00128
compiz (core) - Debug: - x: 0 y: 0 width: 1366 height: 768 border: 134731299, sibling: 0x2e00092
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4188
compiz (core) - Debug: - event window 0x2e00169
compiz (core) - Debug: - x: -7 y: -1 width: 1380 height: 749 border: 32, sibling: 0x0
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4213
compiz (core) - Debug: - event window 0x2e00169
compiz (core) - Debug: - x: -7 y: 26 width: 1380 height: 749 border: 36, sibling: 0x7b4ff4
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4239
compiz (core) - Debug: - event window 0x2e00169
compiz (core) - Debug: - x: -7 y: 26 width: 1380 height: 749 border: 162348208, sibling: 0x2e00128
compiz (core) - Debug: refusing to manage window 0x2e00169
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4188
compiz (core) - Debug: - event window 0x2e00169
compiz (core) - Debug: - x: -7 y: -1 width: 1380 height: 749 border: 32, sibling: 0x0
compiz (core) - Debug: refusing to manage window 0x2e0016b
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4213
compiz (core) - Debug: - event window 0x2e00169
compiz (core) - Debug: - x: -7 y: 26 width: 1380 height: 749 border: 36, sibling: 0x7b4ff4
compiz (core) - Debug: received event:
compiz (core) - Debug: - event serial: 4239
compiz (core) - Debug: - event window 0x2e00169
compiz (core) - Debug: - x: -7 y: 26 width: 1380 height: 749 border: 162348208, sibling: 0x2e00128
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4568
compiz (core) - Debug: - event window 0x2e00169
compiz (core) - Debug: - x: 1 y: 55 width: 1364 height: 712 border: 1, sibling: 0xbfbb6c38
compiz (core) - Debug: pending request:
compiz (core) - Debug: - event serial: 4587
compiz (core) - Debug: - event window 0x2e00169
compiz (core) - Debug: - x: 0 y: 26 width: 1364 height: 712 border: 0, sibling: 0x0

```

---

### Post by TREESofRIGHTEOUSNESS on 2012-05-27
Have you fixed it yet?
were you using CCSM?
I'd suggest using something less prone to break Unity like
[http://www.florian-diesch.de/software/unsettings/](http://www.florian-diesch.de/software/unsettings/)
or
```

sudo apt-get install myunity

```
you will probably need to purge the config files.
Also you can open CCSM in unity 2d or gnome classic and fix whatever needs to be fixed (i.e. check the Unity box, etc...)
hope all works well for you!

---

### Post by several ingredients on 2012-05-29
Thanks for the reply. These last 2 weeks I decided to stop tinkering and just use Windows to get stuff done without any hassle. But today I accessed CCSM in Unity through the terminal. Using CCSM in Gnome/KDE didn't work to reset Unity, the application froze when I tried to do that.

---

