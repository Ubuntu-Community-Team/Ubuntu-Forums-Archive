---
title: "FTL Crashes After Loading Screen"
date: 2014-04-13
forum: Gaming &amp; Leisure
---

### Post by chismend01 on 2014-04-13
Hi.
While playing FTL: Advanced Edition on Steam, I shut down my computer  in-game. When attempting to play the game again, the loading screen  appears. After fully loading, the game crashes. I have attempted to  delete local content and re-installing. I also disabled Steam cloud to see if the fame would then work. These attempts to fix the problem have not worked. FTL was workin nicely before the crash. Once I checked the folder to see  I had deleted I file, I found I was missing the "libstdc++.so." file. What I found interesting is that most people fix the problem by deleting that file, but the file had already been deleted. The profile files in the FTL folder were also not there, possibly corrupted. I think it may be related to an update in my drivers, but I am quite new to Ubuntu. Is there any way to fix this error?

After running the game through the terminal, the debug report showed
       terminate called after throwing an instance of 'std::bad_alloc'
        what():  std::bad_alloc.

Specifications:
Ubuntu 13.10
32 bit
Intel HD Graphics

Thanks for any help.

---

### Post by kostkon on 2014-04-13
Try starting the game from the terminal, like this
```
steam steam://rungameid/212680
```
and check the output; paste it here if you like.

EDIT: Oh, I see you already did that.

---

### Post by chismend01 on 2014-04-13
Sorry, I don't know how to use a spoiler tag on text.
```
Running Steam on ubuntu 13.10 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0413/184111:WARNINGroxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Process 6349 created /quantum-ValveIPCSharedObjects5
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311.30 KB
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Adding licenses for the following package(s): 0, 218, 7932, 8183, 8538, 16589, 17116, 35137
roaming config store loaded successfully - 1899 bytes.
migrating temporary roaming config store
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
ExecCommandLine: "/home/quantum/.local/share/Steam/ubuntu12_32/steam steam://rungameid/212680"
ExecSteamURL: "steam://rungameid/212680"
System startup time: 11.18 seconds
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
OnFocusWindowChanged to window type: k_EWindowTypeSteamDesktop, 0
Generating new string page texture 68: 128x256, total string texture memory is 442.37 KB
Generating new string page texture 72: 384x256, total string texture memory is 835.58 KB
Running Steam on ubuntu 13.10 32-bit
STEAM_RUNTIME has been set by the user to: /home/quantum/.local/share/Steam/ubuntu12_32/steam-runtime
ExecCommandLine: "/home/quantum/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Game update: AppID 212680 "FTL: Faster Than Light", ProcID 6484, IP 0.0.0.0:0
ERROR: ld.so: object '/home/quantum/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
CGameStreamThread: Added instance ID 6484 for appid 212680
CGameStreamThread: Set render instance ID 6484 for appid 212680

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
OnFocusWindowChanged to window type: k_EWindowTypeNonSteamDesktop, 0
ERROR: ld.so: object '/home/quantum/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
/home/quantum/.local/share/Steam/SteamApps/common/FTL Faster Than Light/FTL: line 4: cd: ./data: No such file or directory
CGameStreamThread: Added instance ID 6485 for appid 212680
ERROR: ld.so: object '/home/quantum/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
CGameStreamThread: Added instance ID 6486 for appid 212680
ERROR: ld.so: object '/home/quantum/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/home/quantum/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
CGameStreamThread: Added instance ID 6487 for appid 212680
ERROR: ld.so: object '/home/quantum/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
CGameStreamThread: Added instance ID 6490 for appid 212680
ERROR: ld.so: object '/home/quantum/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/home/quantum/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
CGameStreamThread: Added instance ID 6489 for appid 212680
Loading Arch = x86
CGameStreamThread: Added instance ID 6488 for appid 212680
CGameStreamThread: Added instance ID 6492 for appid 212680
CGameStreamThread: Added instance ID 6493 for appid 212680
ERROR: ld.so: object '/home/quantum/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
Installing breakpad exception handler for appid(steam)/version(1393366296_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(20140225134510_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
CGameStreamThread: Set render instance ID 6487 for appid 212680
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0413/184126:WARNINGroxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
Initializing Crash Catcher...
Initializing Video
Video Initialized
Opengl version = 3.0 Mesa 10.2.0-devel
Starting audio library...
Audio Initialized!
Resource Preload: 14.843
Loading text....
Initializing animations...
Animations Initialized!
Loading Ship Blueprints....
Blueprints Loaded!
Initializing Sound Data....
Generating world...
Loading achievements...
Loading score file...
/home/quantum/.local/share/Steam/SteamApps/common/FTL Faster Than Light/FTL: line 8:  6487 Aborted                 (core dumped) ./FTL "$@"
Game removed: AppID 212680 "FTL: Faster Than Light", ProcID 6487 

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:6349): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

```

---

