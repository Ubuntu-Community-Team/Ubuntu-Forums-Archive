---
title: "Borked Nautilus default icons"
date: 2014-12-28
forum: Desktop Environments
---

### Post by wgw on 2014-12-28
I mucked around with Compiz configuration (font size problem with Google Chrome; but that's another story) and now I have borked the icons that appear in list view with Nautilus: same nondescript icon for files and folders. I tried to reset unity, but got errors out the wazoo (see below).

Where does nautilus pick up its icons? Any way to reset that? I have unity tweak tool and compiz config, but they seem to be loose cannons for me (it seems). 

I have googled and tried things (for instance, I copied nautilus.desktop from a working installation), but no success. (Hmmm, I should really do a log of such searches and post them somewhere: it might be useful to others.)

Suggestions? Thanks for the views!

```
dconf reset -f /org/compiz/
unity --reset-icons


WARN  2014-12-28 12:38:51 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2014-12-28 12:38:51 unity.debug.interface DebugDBusInterface.cpp:216 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory
WARN  2014-12-28 12:38:52 unityct(io) <unknown>:0 Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2014-12-28 12:38:52 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2014-12-28 12:38:52 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2014-12-28 12:38:52 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2014-12-28 12:38:52 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2014-12-28 12:38:52 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
ERROR 2014-12-28 12:38:54 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2014-12-28 12:38:54 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'
```

---

### Post by Frogs Hair on 2014-12-30
Default icon sets are stored in usr/share/icons. You might want to set a default theme not in the tweak tool, but in system settings > appearance . A default icon set should be applied based on the theme selection. If all goes well then you could try customizing with the tweak tool.

---

### Post by wgw on 2014-12-30
Thanks! (Impressive frog!) I discovered that 1) I am already at the default theme (Ambiance) and 2) some of the icons on the system settings page are missing! (Eek!) I'm wondering now whether something worse is going on than a few missing icons. Will do a disk check. 

But, I did poke around and found this in the default directory: 

> [Icon Theme]
Inherits=DMZ-White

DMZ-White only has Name=DMZ (White) and no icons. I will try changing Inherits to gnome; that directory does have all the icons, it seems. 

The real underlying problem for me: no good doc about how all this works. I guess I need an advanced Linux guide....or I need to be more advanced.... The two go hand in hand...

Thanks for your help!

---

### Post by wgw on 2014-12-30
Well, that was easy: switched to Radiance, and everything worked. Switched back to Ambiance and now everything works there too....In the meantime, I have found more themes and a mission: understand how linux works. Thanks for your encouragement.

---

