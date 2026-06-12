---
title: "Steam not running?"
date: 2013-07-10
forum: Gaming &amp; Leisure
---

### Post by bbno3 on 2013-07-10
I have installed Steam through the software centre and through the Terminal and it does not run.
I am using Ubuntu 13.04 and have recently updated my software and Steam.

This is what i get when i try to run Steam through the Terminal
```
Running Steam on ubuntu 13.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1373330809_client)
Installing breakpad exception handler for appid(steam)/version(1373330809_client)
unlinked 0 orphaned pipes
Gtk-Message: Failed to load module "overlay-scrollbar"
Installing breakpad exception handler for appid(steam)/version(1373330809_client)
[0710/122212:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/../common/steam/client_api.cpp (287) : Assertion Failed: ClientAPI_InitGlobalInstance: InternalAPI_Init_Internal failed.

Assert( Assertion Failed: ClientAPI_InitGlobalInstance: InternalAPI_Init_Internal failed.
 ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/../common/steam/client_api.cpp:287

Installing breakpad exception handler for appid(steam)/version(1373330809_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20130710122212_5.dmp
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/SteamStartup.cpp (648) : Assertion Failed: ! "There was a problem with your Steam installation.\n" "Please reinstall steam.\n"
unlinked 2 orphaned pipes
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 59 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 1 multi object alertable sleeps
[2013-07-10 12:22:11] Startup - updater built Apr 30 2013 10:04:24
[2013-07-10 12:22:11] Verifying installation...
[2013-07-10 12:22:11] BVerifyInstalledFiles: ubuntu12_32/steam is 5543712 bytes, expected 5642843
[2013-07-10 12:22:11] Verification complete
[2013-07-10 12:22:11] BRepairInstalledFiles: ignoring bootstrap file ubuntu12_32/steam
Shutting down. . .
[2013-07-10 12:22:12] Shutdown

```

Other then that when ever i run Steam normally i get a box Flash and dissapear so quickly i cannot read it, but i believe it says something like "Please reinstall Steam" which i have done many times, any ideas?

---

### Post by DeathByDenim on 2013-07-10
Does this work?
```
STEAM_RUNTIME=1 steam
```

---

### Post by bbno3 on 2013-07-10
> **DeathByDenim said:**
> Does this work?
```
STEAM_RUNTIME=1 steam
```

No unfortunatly and the output seems to be the same
```
STEAM_RUNTIME=1 steam
Running Steam on ubuntu 13.04 64-bit
STEAM_RUNTIME is enabled by the user
Installing breakpad exception handler for appid(steam)/version(1373330809_client)
Installing breakpad exception handler for appid(steam)/version(1373330809_client)
unlinked 0 orphaned pipes
Gtk-Message: Failed to load module "overlay-scrollbar"
Installing breakpad exception handler for appid(steam)/version(1373330809_client)
[0710/154949:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/../common/steam/client_api.cpp (287) : Assertion Failed: ClientAPI_InitGlobalInstance: InternalAPI_Init_Internal failed.

Assert( Assertion Failed: ClientAPI_InitGlobalInstance: InternalAPI_Init_Internal failed.
 ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/../common/steam/client_api.cpp:287

Installing breakpad exception handler for appid(steam)/version(1373330809_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/assert_20130710154949_5.dmp
/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/steamUI/SteamStartup.cpp (648) : Assertion Failed: ! "There was a problem with your Steam installation.\n" "Please reinstall steam.\n"
unlinked 2 orphaned pipes
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 58 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 1 multi object alertable sleeps
[2013-07-10 15:49:48] Startup - updater built Apr 30 2013 10:04:24
[2013-07-10 15:49:48] Verifying installation...
[2013-07-10 15:49:48] BVerifyInstalledFiles: ubuntu12_32/steam is 5543712 bytes, expected 5642843
[2013-07-10 15:49:48] Verification complete
[2013-07-10 15:49:48] BRepairInstalledFiles: ignoring bootstrap file ubuntu12_32/steam
Shutting down. . .
[2013-07-10 15:49:49] Shutdown


```

---

### Post by DeathByDenim on 2013-07-10
Could you try
```
ldd steam
```
and see if it's maybe missing libraries?

Also, did you try asking at Steam? ( [http://steamcommunity.com/app/221410/discussions/1/](http://steamcommunity.com/app/221410/discussions/1/) )

---

### Post by bbno3 on 2013-07-10
I'm getting 

ldd Steam
ldd: ./Steam: No such file or directory

for the output of that command and i've tried steam in lowercase and it's the same. sorry i can't put it in the code box >.<

and i'll ask there :)

---

### Post by oldos2er on 2013-07-10
> **bbno3 said:**
> Other then that when ever i run Steam normally i get a box Flash and dissapear so quickly i cannot read it, but i believe it says something like "Please reinstall Steam" which i have done many times, any ideas?

Did you uninstall Steam first before reinstalling? If you uninstalled it, did you also delete its folders and files in your home folder? If not, give it a try. ```
rm -rf .steam/*

cd .local/share

rm -rf Steam/*
```

---

### Post by DeathByDenim on 2013-07-10
Oh, sorry, I should have said
```
ldd `which steam`
```

But try oldos2er's suggestion first. That sounds like it would solve your problem.

---

### Post by bbno3 on 2013-07-10
Thanks! the remove folders suggestion worked! thanks guys you truly are amazing! :D

---

