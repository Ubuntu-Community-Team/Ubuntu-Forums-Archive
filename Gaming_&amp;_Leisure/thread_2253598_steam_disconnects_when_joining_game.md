---
title: "steam disconnects when joining game"
date: 2014-11-20
forum: Gaming &amp; Leisure
---

### Post by aramil248 on 2014-11-20
When I go to join someone's game my steam disconnects then reconnects right after.

---

### Post by dannyboy79 on 2014-11-20
launch steam from a terminal so you can see it's std output, see if there's anything being printed to the terminal about why it's disconnecting you from steam when you try to join a friends game. also, what game are you talking about?

---

### Post by aramil248 on 2014-11-21
```
aramil@aramil-desktop:~$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steamwebhelper)/version(20141118120819)
Installing breakpad exception handler for appid(steamwebhelper)/version(1416312499)
Installing breakpad exception handler for appid(steamwebhelper)/version(1416312499)
Installing breakpad exception handler for appid(steamwebhelper)/version(20141118120819)
Installing breakpad exception handler for appid(steamwebhelper)/version(1416312499)
[1121/120519:ERROR:nss_util.cc(1018)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steam)/version(1416350232)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
FillInMachineIDInfo took a total of 0 milliseconds
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311.30 KB
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Adding licenses for the following package(s): 0, 37, 38, 218, 340, 469, 605, 609, 2075, 2806, 4314, 4559, 8183, 8645, 11966, 13054, 15190, 16222, 17304, 17915, 18103, 19007, 21310, 21311, 21472, 26575, 29691, 29856, 30759, 33800, 43160, 43816, 44270, 44273, 48754, 54974, 55143
roaming config store loaded successfully - 5945 bytes.
migrating temporary roaming config store
ExecCommandLine: ""/home/aramil/.local/share/Steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1416350232)
System startup time: 3.97 seconds
Installing breakpad exception handler for appid(steam)/version(1416350232)
[1121/120523:ERROR:renderer_main.cc(227)] Running without renderer sandbox
Generating new string page texture 75: 1024x256, total string texture memory is 1.36 MB
Generating new string page texture 76: 128x256, total string texture memory is 131.07 KB
Generating new string page texture 77: 128x256, total string texture memory is 1.49 MB
Generating new string page texture 78: 64x256, total string texture memory is 1.56 MB
Generating new string page texture 79: 8x256, total string texture memory is 1.56 MB
Generating new string page texture 80: 32x256, total string texture memory is 1.60 MB
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/aramil/.local/share/Steam/ubuntu12_32/steam-runtime
ExecCommandLine: "/home/aramil/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 85: 128x256, total string texture memory is 1.73 MB
Generating new string page texture 86: 256x256, total string texture memory is 1.99 MB
Generating new string page texture 87: 512x256, total string texture memory is 2.51 MB
Generating new string page texture 88: 384x256, total string texture memory is 2.91 MB
Generating new string page texture 90: 128x256, total string texture memory is 3.04 MB
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Generating new string page texture 123: 24x256, total string texture memory is 3.06 MB
Generating new string page texture 124: 16x256, total string texture memory is 3.08 MB
[1121/120533:ERROR:renderer_main.cc(227)] Running without renderer sandbox
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[1121/120540:WARNING:content_browser_client.cc(499)] No browser info matching frame process id 2 and routing id 1
ExecSteamURL: "steam://open/friends"
Generating new string page texture 145: 48x256, total string texture memory is 3.13 MB
Generating new string page texture 146: 128x256, total string texture memory is 3.26 MB
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Generating new string page texture 149: 64x256, total string texture memory is 3.33 MB
Generating new string page texture 150: 256x256, total string texture memory is 3.59 MB
Generating new string page texture 151: 128x256, total string texture memory is 3.72 MB
Installing breakpad exception handler for appid(steam)/version(1416350232)
ExecSteamURL: "steam://rungameid/49520"
Game update: AppID 49520 "Borderlands 2", ProcID 2673, IP 0.0.0.0:0
ERROR: ld.so: object '/home/aramil/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/aramil/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
ERROR: ld.so: object '/home/aramil/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/aramil/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/aramil/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Setting breakpad minidump AppID = 49520
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198025604832 [API loaded no]
ERROR: ld.so: object '/home/aramil/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/aramil/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/aramil/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Installing breakpad exception handler for appid(gameoverlayui)/version(20141118120958)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
[1121/120715:ERROR:renderer_main.cc(227)] Running without renderer sandbox
Installing breakpad exception handler for appid(steam)/version(1416350232)
Game removed: AppID 49520 "Borderlands 2", ProcID 2675 
Inconsistency detected by ld.so: dl-close.c: 762: _dl_close: Assertion `map->l_init_called' failed!
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)
Installing breakpad exception handler for appid(steam)/version(1416350232)


``` the game is Borderlands 2 it also does the same thing with Borderlands the pre-sequel

---

### Post by dannyboy79 on 2014-11-21
ask your friend what his external IP address is and add that in the launch properties box. you right click on borderlands2 within the steam client, select properties, then in the launch options just enter your friends IP like:  74.134.12.16  and that should fix it. at least it did for theatomicass and osirez when they were having issue connecting to me

---

### Post by aramil248 on 2014-11-21
It was already in the launch options when I tried it last time.

---

