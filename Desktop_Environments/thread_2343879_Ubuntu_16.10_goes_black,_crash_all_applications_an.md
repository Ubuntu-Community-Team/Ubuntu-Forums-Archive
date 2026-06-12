---
title: "Ubuntu 16.10 goes black, crash all applications and restarts Unity desktop."
date: 2016-11-20
forum: Desktop Environments
---

### Post by Micski on 2016-11-20
Without warning, monitors goes black for a few seconds, dumps all applications and a clean Unity desktop appears. All running applications gone. I think, Unity and Compiz crashes and restarts. I suspect, it might be related to use of VirtualBox as a host for other guest systems. I show the system log below. Computer is running Ubuntu 16.10 on Gigabyte motherboard with Intel H62 chipset, Intel Core i5-2500 CPU, 8 GB DDR3 RAM and SSD.
```
Nov 19 19:38:25 ws kernel: [14120.864481] perf: interrupt took too long (2516 > 2500), lowering kernel.perf_event_max_sample_rate to 79250Nov 19 19:41:39 ws unity-panel-ser[2395]: unable to fetch album art: Operation not supported
Nov 19 19:42:48 ws unity-panel-ser[2395]: window_menu_model_new: assertion 'BAMF_IS_APPLICATION(app)' failed
Nov 19 19:42:48 ws unity-panel-ser[2395]: track_menus: assertion 'IS_WINDOW_MENU(menus)' failed
Nov 19 19:42:49 ws compiz[2374]: intel_do_flush_locked failed: Bad address
Nov 19 19:42:50 ws systemd[1855]: unity7.service: Main process exited, code=exited, status=1/FAILURE
Nov 19 19:42:50 ws compiz[2374]: [2663:2663:1119/194250:ERROR:zygote_communication_linux.cc(292)] Failed to send GetTerminationStatus message to zygote
Nov 19 19:42:50 ws compiz[2374]: message repeated 4 times: [ [2663:2663:1119/194250:ERROR:zygote_communication_linux.cc(292)] Failed to send GetTerminationStatus message to zygote]
Nov 19 19:42:55 ws systemd[1855]: unity7.service: Unit entered failed state.
Nov 19 19:42:55 ws systemd[1855]: unity7.service: Failed with result 'exit-code'.
Nov 19 19:42:55 ws systemd[1855]: unity7.service: Service hold-off time over, scheduling restart.
Nov 19 19:42:55 ws systemd[1855]: Stopped target User systemd services for the Ubuntu graphical session.
Nov 19 19:42:55 ws systemd[1855]: Stopping User systemd services for the Ubuntu graphical session.
Nov 19 19:42:55 ws systemd[1855]: Stopped Unity Shell v7.
Nov 19 19:42:55 ws systemd[1855]: Starting Unity Shell v7...
Nov 19 19:42:55 ws compiz-profile-selector[6814]: OpenGL vendor string:   Intel Open Source Technology Center
Nov 19 19:42:55 ws compiz-profile-selector[6814]: OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop
Nov 19 19:42:55 ws compiz-profile-selector[6814]: OpenGL version string:  3.0 Mesa 12.0.3
Nov 19 19:42:55 ws compiz-profile-selector[6814]: Not software rendered:    #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: Not blacklisted:          #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: GLX fbconfig:             #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: GLX texture from pixmap:  #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: GL npot or rect textures: #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: GL vertex program:        #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: GL fragment program:      #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: GL vertex buffer object:  #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: GL framebuffer object:    #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: GL version is 1.4+:       #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: Unity 3D supported:       #033[32;01myes#033[00m
Nov 19 19:42:55 ws compiz-profile-selector[6814]: Using compiz profile 'ubuntu'
Nov 19 19:42:55 ws compiz-profile-selector[6814]: dbus-update-activation-environment: setting COMPIZ_CONFIG_PROFILE=ubuntu
Nov 19 19:42:55 ws compiz-profile-selector[6814]: compizconfig - Info: Backend     : gsettings
Nov 19 19:42:55 ws compiz-profile-selector[6814]: compizconfig - Info: Integration : true
Nov 19 19:42:55 ws compiz-profile-selector[6814]: compizconfig - Info: Profile     : unity
Nov 19 19:42:55 ws systemd[1855]: Started Unity Shell v7.
Nov 19 19:42:55 ws systemd[1855]: Reached target User systemd services for the Ubuntu graphical session.
Nov 19 19:42:55 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: core
Nov 19 19:42:55 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: core
Nov 19 19:42:55 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: ccp
Nov 19 19:42:55 ws unity-panel-ser[2395]: menus_destroyed: assertion 'IS_WINDOW_MENU(wm)' failed
Nov 19 19:42:55 ws unity-panel-ser[2395]: menus_destroyed: assertion 'IS_WINDOW_MENU(wm)' failed
Nov 19 19:42:55 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: ccp
Nov 19 19:42:55 ws unity-panel-ser[2395]: menus_destroyed: assertion 'IS_WINDOW_MENU(wm)' failed
Nov 19 19:42:55 ws unity-panel-ser[2395]: message repeated 5 times: [ menus_destroyed: assertion 'IS_WINDOW_MENU(wm)' failed]
Nov 19 19:42:55 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: composite
Nov 19 19:42:55 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: composite
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: opengl
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: opengl
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/Compiz (opengl) - Info: GLX_EXT_buffer_age is supported
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: compiztoolbox
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: compiztoolbox
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: grid
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: grid
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: wall
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: wall
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: place
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: place
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: copytex
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: copytex
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: imgpng
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: imgpng
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: mousepoll
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: mousepoll
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: vpswitch
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: vpswitch
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: commands
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: commands
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: resize
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: resize
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: move
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: move
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: regex
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: regex
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: unitymtgrabhandles
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: unitymtgrabhandles
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: snap
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: snap
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: session
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: session
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: animation
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: animation
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: expo
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: expo
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: ezoom
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: ezoom
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: workarounds
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: workarounds
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: fade
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: fade
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: scale
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: scale
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Loading plugin: unityshell
Nov 19 19:42:56 ws compiz[6823]: /usr/bin/compiz (core) - Info: Starting plugin: unityshell
Nov 19 19:42:56 ws compiz[6823]: compizconfig - Info: Backend     : gsettings
Nov 19 19:42:56 ws compiz[6823]: compizconfig - Info: Integration : true
Nov 19 19:42:56 ws compiz[6823]: compizconfig - Info: Profile     : unity
Nov 19 19:42:56 ws compiz[6823]: WARN  2016-11-19 19:42:56 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
Nov 19 19:42:57 ws compiz[6823]: WARN  2016-11-19 19:42:57 unity.debug.interface DebugDBusInterface.cpp:217 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory -- full D-Bus introspection will not be available
Nov 19 19:42:57 ws compiz[6823]: WARN  2016-11-19 19:42:57 xim.controller XIMController.cpp:103 IBus natively supported.
Nov 19 19:42:57 ws compiz[6823]: WARN  2016-11-19 19:42:57 unity.dash.gsettingsscopereader GSettingsScopes.cpp:108 Error fetching protocol metadata for scope: social.scope : Valid key file could not be found in search dirs
Nov 19 19:42:57 ws compiz[6823]: WARN  2016-11-19 19:42:57 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
Nov 19 19:42:57 ws compiz[6823]: WARN  2016-11-19 19:42:57 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
Nov 19 19:42:57 ws compiz[6823]: WARN  2016-11-19 19:42:57 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
Nov 19 19:42:57 ws compiz[6823]: ERROR 2016-11-19 19:42:57 unityo (appinfo2) <unknown>:0 g_dbus_proxy_new_for_bus: assertion 'g_variant_is_object_path (object_path)' failed
Nov 19 19:42:57 ws compiz[6823]: WARN  2016-11-19 19:42:57 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
Nov 19 19:42:57 ws compiz[6823]: WARN  2016-11-19 19:42:57 unity.glib.dbus.server GLibDBusServer.cpp:593 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
Nov 19 19:42:57 ws unity-panel-ser[2395]: window_menu_model_new: assertion 'BAMF_IS_APPLICATION(app)' failed
Nov 19 19:42:57 ws unity-panel-ser[2395]: track_menus: assertion 'IS_WINDOW_MENU(menus)' failed
Nov 19 19:42:57 ws compiz[6823]: ERROR 2016-11-19 19:42:57 unity.glib.dbus.server GLibDBusServer.cpp:538 DBus name lost 'org.gnome.Shell'
Nov 19 19:42:57 ws compiz[6823]: ERROR 2016-11-19 19:42:57 unity.glib.dbus.server GLibDBusServer.cpp:538 DBus name lost 'com.canonical.Unity'
Nov 19 19:42:57 ws compiz[6823]: WARN  2016-11-19 19:42:57 unity.key.gnome.grabber GnomeKeyGrabber.cpp:108 Trying to grab a disabled action, we skip it
Nov 19 19:42:57 ws compiz[6823]: message repeated 9 times: [ WARN  2016-11-19 19:42:57 unity.key.gnome.grabber GnomeKeyGrabber.cpp:108 Trying to grab a disabled action, we skip it]
Nov 19 19:43:18 ws unity-panel-ser[2395]: window_menu_model_new: assertion 'BAMF_IS_APPLICATION(app)' failed
Nov 19 19:43:18 ws unity-panel-ser[2395]: track_menus: assertion 'IS_WINDOW_MENU(menus)' failed
Nov 19 19:43:19 ws dbus-daemon[1884]: Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service'
Nov 19 19:43:19 ws systemd[1855]: Starting GNOME Terminal Server...
Nov 19 19:43:19 ws dbus-daemon[1884]: Successfully activated service 'org.gnome.Terminal'
Nov 19 19:43:19 ws systemd[1855]: Started GNOME Terminal Server.
Nov 19 19:43:22 ws gnome-terminal-[6856]: Allocating size to GtkBox 0x55ad8c9f77b0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
```

---

### Post by Micski on 2016-12-06
[COLOR=#000000]Is it possible, that someone could look at this?[/COLOR]

---

### Post by Vdragon on 2017-05-23
[FONT=monospace][COLOR=#000000]```
intel_do_flush_locked failed: Bad address
```

Likely an OpenGL Graphics Driver(for Intel, it's in Mesa) issue, the workaround is switch desktop environments that are not using OpenGL rendering(like XFCE or LXDE)
[/COLOR]
Please check out intel linux graphics page for troubleshooting[/FONT]

---

