---
title: "Unity Plugin conflicts with Compiz modifications"
date: 2017-01-27
forum: Desktop Environments
---

### Post by UbuntuWho on 2017-01-27
I realize that Ubuntu 16.04's Unity Desktop Environment relies heavily on Compiz (I have version 0.9.12.1). I adjusted some settings so the panel would appear on the bottom. That made the Expo effect look strange, as the viewports look "squeezed". I check the settings, and the Y bottom offset is set to 48. I change this to 0. I then enable some plugins. ...Wait! Where'd my desktop go? After enabling some benign plugins (like crash handler), the desktop disappears for as long as thirty seconds, then reappears. I moved my cursor to the corner I set for Expo to appear. Why is everything so mushed again? I check my settings - the Y bottom offset is 48 again! Buuuut this doesn't just happens when I enable or disable Compiz plugins,** it happens when I log out and in again, too! **](*,)

This isn't the only issue. Windows don't seem to focus properly no matter what I do to fix them. This happens in the Expo and in the panel. Clicking on windows in Expo to switch to where the window is brings me back to the viewport I already was in. Moving a window in Expo, usually one that is maximized, to another viewport doesn't work. And, *in Unity's own panel*, when I click on an icon of an opened application, it does nothing.

Through several tests under XFCE, Compiz and every plugin *BUT THE UNITY PLUGIN* works fine. I want to customize Unity the way I want it to look, but I can't seem to resolve the conflicts between Unity and the other plugins, even the plugins it requires by default! I realize that some plugins can't be enabled because of the Unity plugin, but there should be some way of being able to manipulate Compiz without Unity crashing!

---

### Post by UbuntuWho on 2017-01-28
I figure that a terminal output may be needed, so I started Compiz under XFCE:
```
$ compiz --replace
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : ini
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
compiz (core) - Info: Loading plugin: crashhandler
compiz (core) - Info: Starting plugin: crashhandler
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: imgjpeg
compiz (core) - Info: Starting plugin: imgjpeg
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: wobbly
compiz (core) - Info: Starting plugin: wobbly
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: imgsvg
compiz (core) - Info: Starting plugin: imgsvg
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (core) - Info: Stopping plugin: scale
compiz (core) - Info: Stopping plugin: expo
compiz (core) - Info: Stopping plugin: imgsvg
compiz (core) - Info: Stopping plugin: move
compiz (core) - Info: Stopping plugin: fade
compiz (core) - Info: Stopping plugin: place
compiz (core) - Info: Stopping plugin: imgpng
compiz (core) - Info: Stopping plugin: wobbly
compiz (core) - Info: Stopping plugin: resize
compiz (core) - Info: Stopping plugin: grid
compiz (core) - Info: Stopping plugin: imgjpeg
compiz (core) - Info: Stopping plugin: decor
compiz (core) - Info: Stopping plugin: compiztoolbox
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Starting plugin: imgsvg
compiz (core) - Info: Starting plugin: imgjpeg
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Starting plugin: wobbly
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Starting plugin: scale

```

I started the Unity plugin. I know it's a bit sacrilegious to run Unity on XFCE, but it works... not without errors, though:

```

compiz (core) - Info: Unloading plugin: decor
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2017-01-28 04:12:21 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:12:22 unity.debug.interface DebugDBusInterface.cpp:217 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory -- full D-Bus introspection will not be available
WARN  2017-01-28 04:12:24 unity.dash.gsettingsscopereader GSettingsScopes.cpp:108 Error fetching protocol metadata for scope: social.scope : Valid key file could not be found in search dirs
WARN  2017-01-28 04:12:27 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:12:28 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:12:28 nux.inputmethod.ibus InputMethodIBus.cpp:67 Impossible to connect to connect to ibus
WARN  2017-01-28 04:12:29 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:12:29 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:12:29 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
ERROR 2017-01-28 04:12:33 unity.glib.dbus.server GLibDBusServer.cpp:538 DBus name lost 'org.gnome.Shell'
ERROR 2017-01-28 04:12:33 unity.glib.dbus.server GLibDBusServer.cpp:538 DBus name lost 'com.canonical.Unity'
WARN  2017-01-28 04:12:33 unity.glib.dbus.proxy GLibDBusProxy.cpp:487 Calling method "CanShutdown" on object path: "/org/gnome/SessionManager" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
ERROR 2017-01-28 04:12:33 unity.session.gnome GnomeSessionManager.cpp:383 Gnome Session call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
WARN  2017-01-28 04:13:08 nux.inputmethod.ibus InputMethodIBus.cpp:67 Impossible to connect to connect to ibus

```

I then disable a plugin that shouldn't conflict... let's try "Crash Handler":
```
compiz (core) - Info: Stopping plugin: unityshell
ERROR 2017-01-28 04:16:22 unity.shell.compiz unityshell.cpp:4025 Impossible to delete the unity locked stamp file

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed

(compiz:8841): GLib-CRITICAL **: g_hash_table_remove_internal: assertion 'hash_table != NULL' failed
compiz (core) - Info: Stopping plugin: scale
compiz (core) - Info: Stopping plugin: expo
compiz (core) - Info: Stopping plugin: fade
compiz (core) - Info: Stopping plugin: imgpng
compiz (core) - Info: Stopping plugin: wobbly
compiz (core) - Info: Stopping plugin: resize
compiz (core) - Info: Stopping plugin: grid
compiz (core) - Info: Stopping plugin: imgjpeg
compiz (core) - Info: Stopping plugin: imgsvg
compiz (core) - Info: Stopping plugin: move
compiz (core) - Info: Stopping plugin: compiztoolbox
compiz (core) - Info: Stopping plugin: place
compiz (core) - Info: Stopping plugin: opengl
compiz (core) - Info: Stopping plugin: composite
compiz (core) - Info: Stopping plugin: crashhandler
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Starting plugin: imgsvg
compiz (core) - Info: Starting plugin: imgjpeg
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Starting plugin: wobbly
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Starting plugin: unityshell
ERROR 2017-01-28 04:16:23 unity.wm.compiz PluginAdapter.cpp:66 Already Initialized!
WARN  2017-01-28 04:16:23 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:16:23 unity.debug.interface DebugDBusInterface.cpp:217 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory -- full D-Bus introspection will not be available
WARN  2017-01-28 04:16:23 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:16:23 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:16:23 nux.inputmethod.ibus InputMethodIBus.cpp:67 Impossible to connect to connect to ibus
WARN  2017-01-28 04:16:23 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:16:23 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2017-01-28 04:16:23 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
Segmentation fault (core dumped)

```

Then Compiz restarts. This happens when I'm *in* Unity, not because I'm running a different desktop environment. :(

---

### Post by mc4man on 2017-01-28
Re: the  expo offsets
These values are automatically set depending on whether the launcher is on left or bottom & the size chosen for launcher icons.
When using a bottom launcher the bottom offset is by default set to 64px and the x offset set to 0 , the value  of the bottom offset would be increased or decreased if the user raises or lowers the size of the launcher icon. 
When using left launcher it would by default be bottom offset of 0 & x offset of 64, ect.
The  reason is so when in expo (using the default of Wall) the Ws's don't go behind the launcher.

Can't see why you'd want to alter this, it's also possible that on login it's going to read launcher position & icon size & set appropriately no matter what you've done.

As far as that compiz crash plugin - yeah, enabling it seems to crash compiz. Overall the plugin is worthless in an ubuntu session so no reason to use it.

---

### Post by UbuntuWho on 2017-01-29
> **mc4man said:**
> 
These values are automatically set depending on whether the launcher is on left or bottom & the size chosen for launcher icons.

Can't see why you'd want to alter this, it's also possible that on login it's going to read launcher position & icon size & set appropriately no matter what you've done.

The Y bottom offset value is more of an aesthetic issue. When the Y bottom offset for Expo is set to the panel size, the viewports look squished, and maximized windows hang outside the bottoms of them. By setting the value to 0, everything appears in the viewports as it would on my desktop, and no window hangs out. If I can override the default value, then Expo won't keep setting it back.

As for the crash handler, that's just an example. I could enable several plugins that shouldn't conflict with the Unity Plugin and cause Compiz to crash. That's more of a serious issue, I think. Do you need more info? :confused:

**EDIT: **Reviewing the moment of the crash, I noticed that it output **[FONT=courier new]unity.shell.compiz unityshell.cpp:4025 Impossible to delete the unity locked stamp file[/FONT]** and yet later on upon loading it outputs  **[FONT=courier new]unity.wm.compiz PluginAdapter.cpp:66 Already Initialized![/FONT]** Is it possible that Unity is having trouble unloading completely?

---

### Post by UbuntuWho on 2017-02-23
Is anyone else trying to configure Compiz under Ubuntu Unity? Does anyone else have this problem, or is it just me? Is it possible to tweak the Unity plugin to get the desired effect? I'm really interested to know what you can and can't do under Unity, because I want to be able to make Unity work better with Compiz. :-k

EDIT: I'm still on XFCE. I've been having so many issues with the aesthetics of Unity that I decided to use another desktop environment; however, I really liked Unity. :(

---

### Post by UbuntuWho on 2017-09-12
Apparently, there's no fix, and nobody's willing to fix this, so I'm marking it as solved. Even though it isn't. :(

---

