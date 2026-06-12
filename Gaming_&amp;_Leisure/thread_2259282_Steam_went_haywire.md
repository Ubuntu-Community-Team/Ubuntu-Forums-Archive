---
title: "Steam went haywire"
date: 2015-01-03
forum: Gaming &amp; Leisure
---

### Post by lastopier on 2015-01-03
When I tried to run it, it said I was missing some i386 packages...so I installed them...and now it says this:
```
Running Steam on ubuntu 14.10 64-bit
STEAM_RUNTIME is disabled by the user
Installing breakpad exception handler for appid(steam)/version(1416617579)
Installing breakpad exception handler for appid(steam)/version(1416617579)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steamwebhelper)/version(20141121162341)
Installing breakpad exception handler for appid(steamwebhelper)/version(1416587021)
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
Installing breakpad exception handler for appid(steamwebhelper)/version(20141121162341)
Installing breakpad exception handler for appid(steamwebhelper)/version(1416587021)
Installing breakpad exception handler for appid(steamwebhelper)/version(1416587021)
Installing breakpad exception handler for appid(steam)/version(1416617579)
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/vgui2/src/../vgui_surfacelib/FontManager.cpp (276) : Assertion Failed: descs.Count() >= 1
Assert( Assertion Failed: descs.Count() >= 1 ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/vgui2/src/../vgui_surfacelib/FontManager.cpp:276

Installing breakpad exception handler for appid(steam)/version(1416617579)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20150103160545_5.dmp
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/vgui2/src/../vgui_surfacelib/FontManager.cpp (276) : Assertion Failed: descs.Count() >= 1
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/vgui2/src/../vgui_surfacelib/FontManager.cpp (276) : Assertion Failed: descs.Count() >= 1
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/vgui2/src/../vgui_surfacelib/FontManager.cpp (276) : Assertion Failed: descs.Count() >= 1
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/../common/steam/client_api.cpp (322) : Assertion Failed: ClientAPI_InitGlobalInstance: InternalAPI_Init_Internal failed, most likely because you are missing a 32-bit dependency of steamclient.so (the Steam client is a 32-bit app).

/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/SteamStartup.cpp (772) : Assertion Failed: ! "There was a problem with your Steam installation.\n" "Please reinstall steam.\n"
Requested Force create but SharedObjectMutex already created
Forced create but already created for SharedObjectEvent
Forced create but already created for SharedObjectEvent
[2015-01-03 16:05:44] Startup - updater built Nov 21 2014 16:23:41
[2015-01-03 16:05:44] Verifying installation...
[2015-01-03 16:05:44] Verification complete
[2015-01-03 16:05:46] Shutdown


```

PS: Just to make sure, I reinstalled Steam several times

---

### Post by lastopier on 2015-01-04
Ok, so, I solved this by deleting libstdc++.so.6 and libstdc++.so.6.something from ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu
Somehow, it just seems to work now(it didn't work before)

---

