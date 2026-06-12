---
title: "steam wont start"
date: 2015-06-18
forum: Gaming &amp; Leisure
---

### Post by dragonknight2010 on 2015-06-18
sooo steam wouldnt work for me so i went online found a forum saying to install 32b libs now when i click on steam it wont even start up no error from before nothing...any help guys?


swazi71@swazi71Comp:~$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1433441724)
Installing breakpad exception handler for appid(steam)/version(1433441724)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1433441724)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
/home/swazi71/.local/share/Steam/ubuntu12_32/steamwebhelper: error while loading shared libraries: libcap.so.2: cannot open shared object file: No such file or directory
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/../common/steam/client_api.cpp (320) : Assertion Failed: ClientAPI_InitGlobalInstance: InternalAPI_Init_Internal failed, most likely because you are missing a 32-bit dependency of steamclient.so (the Steam client is a 32-bit app).


Assert( Assertion Failed: ClientAPI_InitGlobalInstance: InternalAPI_Init_Internal failed, most likely because you are missing a 32-bit dependency of steamclient.so (the Steam client is a 32-bit app).
 ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/../common/steam/client_api.cpp:320


Installing breakpad exception handler for appid(steam)/version(1433441724)
assert_20150618002242_5.dmp[6353]: Uploading dump (out-of-process)
/tmp/dumps/assert_20150618002242_5.dmp
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/SteamStartup.cpp (751) : Assertion Failed: ! "There was a problem with your Steam installation.\n" "Please reinstall steam.\n"
assert_20150618002242_5.dmp[6353]: Finished uploading minidump (out-of-process): success = no
assert_20150618002242_5.dmp[6353]: error: HTTP response code said error
assert_20150618002242_5.dmp[6353]: file ''/tmp/dumps/assert_20150618002242_5.dmp'', upload no: ''HTTP response code said error''
[2015-06-18 00:22:41] Startup - updater built Jun  4 2015 10:35:42
[2015-06-18 00:22:41] Verifying installation...
[2015-06-18 00:22:41] Verification complete
[2015-06-18 00:22:43] Shutdown

---

