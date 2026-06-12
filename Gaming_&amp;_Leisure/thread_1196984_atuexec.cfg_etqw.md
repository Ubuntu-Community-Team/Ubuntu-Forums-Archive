---
title: "atuexec.cfg etqw"
date: 2009-06-25
forum: Gaming &amp; Leisure
---

### Post by deadmnky on 2009-06-25
has anyone else had the issue of adding an autoexec.cfg file to the /.etqwcl/sdnet/NAME/base folder causing errors when trying to start up etqw after the fact.
everything works great until i add the file. i can even use console commands that are in the config file i am trying to add.
i am using jaunty with a bfg 98gt and 4gig of ram on a phenom triple 2.4ghz cpu.
the errors i get are as follows

./etqw-rthread

```
ETQW 1.5.12663.12663  linux-x86 May  9 2008 13:57:26
found interface lo - loopback
found interface eth0 - 192.168.0.112/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/deadmnky/etqw/base/game000.pk4 with checksum 0x3efd73a5
Loaded pk4 /home/deadmnky/etqw/base/game001.pk4 with checksum 0xa02f1c18
Loaded pk4 /home/deadmnky/etqw/base/game002.pk4 with checksum 0x87457e61
Loaded pk4 /home/deadmnky/etqw/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /home/deadmnky/etqw/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /home/deadmnky/etqw/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /home/deadmnky/etqw/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /home/deadmnky/etqw/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /home/deadmnky/etqw/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /home/deadmnky/etqw/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /home/deadmnky/etqw/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /home/deadmnky/etqw/base/pak008.pk4 with checksum 0x71a93b80
Loaded pk4 /home/deadmnky/etqw/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /home/deadmnky/etqw/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /home/deadmnky/etqw/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /home/deadmnky/etqw/base/zpak_english003.pk4 with checksum 0xc2d7ed49
Loaded pk4 /home/deadmnky/etqw/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /home/deadmnky/etqw/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /home/deadmnky/etqw/base/zpak_french003.pk4 with checksum 0x8f315c7b
Loaded pk4 /home/deadmnky/etqw/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /home/deadmnky/etqw/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /home/deadmnky/etqw/base/zpak_german003.pk4 with checksum 0x370e6186
Loaded pk4 /home/deadmnky/etqw/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /home/deadmnky/etqw/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /home/deadmnky/etqw/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /home/deadmnky/etqw/base/zpak_korean003.pk4 with checksum 0x4f8dfac1
Loaded pk4 /home/deadmnky/etqw/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /home/deadmnky/etqw/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /home/deadmnky/etqw/base/zpak_polish003.pk4 with checksum 0x8d9af876
Loaded pk4 /home/deadmnky/etqw/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /home/deadmnky/etqw/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /home/deadmnky/etqw/base/zpak_russian003.pk4 with checksum 0x7e90b040
Loaded pk4 /home/deadmnky/etqw/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /home/deadmnky/etqw/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Loaded pk4 /home/deadmnky/etqw/base/zpak_spanish003.pk4 with checksum 0xe7d989bc
Current search path:
/home/deadmnky/.etqwcl/base
/home/deadmnky/etqw/base
/home/deadmnky/etqw/base/zpak_spanish003.pk4 (6 files)
/home/deadmnky/etqw/base/zpak_spanish002.pk4 (119 files)
/home/deadmnky/etqw/base/zpak_spanish001.pk4 (13 files)
/home/deadmnky/etqw/base/zpak_russian003.pk4 (5 files)
/home/deadmnky/etqw/base/zpak_russian002.pk4 (119 files)
/home/deadmnky/etqw/base/zpak_russian001.pk4 (13 files)
/home/deadmnky/etqw/base/zpak_polish003.pk4 (6 files)
/home/deadmnky/etqw/base/zpak_polish002.pk4 (119 files)
/home/deadmnky/etqw/base/zpak_polish001.pk4 (13 files)
/home/deadmnky/etqw/base/zpak_korean003.pk4 (5 files)
/home/deadmnky/etqw/base/zpak_korean002.pk4 (12 files)
/home/deadmnky/etqw/base/zpak_korean001.pk4 (12 files)
/home/deadmnky/etqw/base/zpak_korean000.pk4 (6 files)
/home/deadmnky/etqw/base/zpak_german003.pk4 (5 files)
/home/deadmnky/etqw/base/zpak_german002.pk4 (119 files)
/home/deadmnky/etqw/base/zpak_german001.pk4 (13 files)
/home/deadmnky/etqw/base/zpak_french003.pk4 (14 files)
/home/deadmnky/etqw/base/zpak_french002.pk4 (119 files)
/home/deadmnky/etqw/base/zpak_french001.pk4 (13 files)
/home/deadmnky/etqw/base/zpak_english003.pk4 (7 files)
/home/deadmnky/etqw/base/zpak_english002.pk4 (117 files)
/home/deadmnky/etqw/base/zpak_english001.pk4 (9 files)
/home/deadmnky/etqw/base/zpak_english000.pk4 (1018 files)
/home/deadmnky/etqw/base/pak008.pk4 (1496 files)
/home/deadmnky/etqw/base/pak007.pk4 (1510 files)
/home/deadmnky/etqw/base/pak006.pk4 (3 files)
/home/deadmnky/etqw/base/pak005.pk4 (2172 files)
/home/deadmnky/etqw/base/pak004.pk4 (72 files)
/home/deadmnky/etqw/base/pak003.pk4 (1133 files)
/home/deadmnky/etqw/base/pak002.pk4 (1637 files)
/home/deadmnky/etqw/base/pak001.pk4 (1067 files)
/home/deadmnky/etqw/base/pak000.pk4 (9350 files)
/home/deadmnky/etqw/base/game002.pk4 (3 files)
/home/deadmnky/etqw/base/game001.pk4 (11 files)
/home/deadmnky/etqw/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3566Kb
------------------------------
execing 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
thread priority set to 1
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1680x1050
SDL_ListModes:
1680x1050 1600x1024 1440x900 1400x1050 1360x768 1280x1024 1280x960 1280x720 1152x864 1024x768 960x600 
960x540 840x525 832x624 800x600 800x512 720x450 700x525 680x384 640x512 640x480 
576x432 512x384 416x312 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
------- Initializing renderSystem --------
----- R_InitOpenGL -----
signal caught: 'Segmentation fault', si_code 1
callstack:
0x0
[0x082e6001]
[0x082e340d]
[0xf7eee410]
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()

```

and with ./etqw-rthread.x86
```
./etqw-rthread.x86: error while loading shared libraries: libSDL-1.2.id.so.0: cannot open shared object file: No such file or directory

```

i can look at the file in the game folder everyone can read and write to it as well so i have no clue what is wrong with any help would be appreciated until then i guess i will continue my search
thanks

---

