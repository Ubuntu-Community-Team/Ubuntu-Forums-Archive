---
title: "Steam does not create system starters for some games"
date: 2013-04-17
forum: Gaming &amp; Leisure
---

### Post by yauu on 2013-04-17
For some games I installed, steam hasn't created system starters. So I  can't access them from the system software menu, and I can't search for  them in the program search. How can I force Steam to create these  launchers?


I started steam from the terminal, the output is shown  below. I tried to create a shortcut for a game that already had won, and  then the following message came: "A shortcut has been created and  placed on your desktop". Wen I then wanted to create a shortcut for a  game that had none, the message was: "Could not create shortcut. A  shortcut to this game is probably already on the desktop.


Here's the output of the terminal:

```



Running Steam on ubuntu 12.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
unlinked 0 orphaned pipes
Gtk-Message: Failed to load module "overlay-scrollbar"

(steam:3247): Gtk-WARNING **: Im Modulpfad »adwaita« konnte keine Themen-Engine gefunden werden,
/usr/share/themes/Adwaita/gtk-2.0/gtkrc:989: error: unexpected identifier `direction', expected character `}'
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
[0416/155018:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Process 3247 created /ampa-ValveIPCSharedObjects3
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Generating new string page texture 2: 48x256, total string texture memory is 49,15 KB
Generating new string page texture 3: 384x256, total string texture memory is 442,37 KB
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Installing breakpad exception handler for appid(steam)/version(1364601080_client)
Adding license for package 0
Adding license for package 64
Adding license for package 110
Adding license for package 242
Adding license for package 2275
Adding license for package 2529
roaming config store loaded successfully - 448 bytes.
migrating temporary roaming config store
ExecCommandLine: "/home/ampa/.local/share/Steam/ubuntu12_32/steam"
`menu_proxy_module_load': /home/ampa/.local/share/Steam/ubuntu12_32/steam: undefined symbol: menu_proxy_module_load

(steam:3247): Gtk-WARNING **: Failed to load type module: (null)

Generating new string page texture 71: 1024x256, total string texture memory is 1,49 MB
Generating new string page texture 72: 128x256, total string texture memory is 131,07 KB
Generating new string page texture 73: 128x256, total string texture memory is 1,62 MB
Generating new string page texture 74: 256x256, total string texture memory is 1,88 MB
Generating new string page texture 75: 32x256, total string texture memory is 1,92 MB
Generating new string page texture 76: 64x256, total string texture memory is 1,98 MB

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

 (steam:3247): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

Installing breakpad exception handler for appid(steam)/version(1364601080_client)
System startup time: 38,23 seconds
Generating new string page texture 79: 24x256, total string texture memory is 2,01 MB
Generating new string page texture 80: 128x256, total string texture memory is 2,14 MB
Generating new string page texture 81: 8x256, total string texture memory is 2,15 MB
Running Steam on ubuntu 12.10 64-bit
STEAM_RUNTIME has been set by the user to: /home/ampa/.local/share/Steam/ubuntu12_32/steam-runtime
CAPIJobRequestUserStats - Server response failed 2
ExecCommandLine: "/home/ampa/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 88: 512x256, total string texture memory is 2,67 MB
Generating new string page texture 91: 128x256, total string texture memory is 2,80 MB
Generating new string page texture 93: 256x256, total string texture memory is 3,06 MB
Generating new string page texture 96: 16x256, total string texture memory is 3,08 MB
Generating new string page texture 97: 256x256, total string texture memory is 3,34 MB
Generating new string page texture 112: 48x256, total string texture memory is 3,39 MB
Generating new string page texture 95: 128x256, total string texture memory is 3,52 MB
unlinked 2 orphaned pipes
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 368113 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 7 multi object alertable sleeps
[2013-04-16 15:50:14] Startup - updater built Mar 29 2013 11:40:39
[2013-04-16 15:50:14] Verifying installation...
[2013-04-16 15:50:15] Verification complete
Shutting down. . .
[2013-04-16 15:56:48] Shutdown




```


I have this problem with 2 Games, darwinia and uplink. I installed 8 Games with steam.

---

