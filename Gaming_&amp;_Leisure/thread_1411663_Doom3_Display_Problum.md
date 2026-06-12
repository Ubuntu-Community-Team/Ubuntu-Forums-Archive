---
title: "Doom3 Display Problum"
date: 2010-02-20
forum: Gaming &amp; Leisure
---

### Post by Paul Lynch on 2010-02-20
Hi, 
complete noob here, I  am having difficulty running doom3. I have installed the game as instructed on a number of sites and copied the pk4 files (01,2,3,4) to the base folder. When I run the script file my monitor goes blank but I can hear the game over my system speakers (poor quality sound but that is another days problem!). I have spent a number of hours going through previous threads here and have not yet solved my prob.  Any help would be appreciated at this stage!!

I am using a NV44A Geforce 6200 card and I have the Ubuntu proprietary drivers installed (Version 173)

My problem seems to be:

WARNING: Couldn't load image: textures/black
WARNING: Couldn't load image: textures/sfx/monitor_glass2

Just not sure where to start ...... HELP!


DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:53:29
found interface lo - loopback
found interface eth0 - 87.198.44.148/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/paul/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /home/paul/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /home/paul/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /home/paul/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /home/paul/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /home/paul/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/paul/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/paul/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/paul/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/paul/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /home/paul/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/paul/.doom3/base
/home/paul/doom3/base
/home/paul/doom3/base/pak008.pk4 (3 files)
/home/paul/doom3/base/pak007.pk4 (38 files)
/home/paul/doom3/base/pak006.pk4 (48 files)
/home/paul/doom3/base/pak005.pk4 (63 files)
/home/paul/doom3/base/pak003.pk4 (4676 files)
/home/paul/doom3/base/pak002.pk4 (6120 files)
/home/paul/doom3/base/pak001.pk4 (8972 files)
/home/paul/doom3/base/pak000.pk4 (2698 files)
/home/paul/doom3/base/game03.pk4 (2 files)
/home/paul/doom3/base/game02.pk4 (2 files)
/home/paul/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
WARNING: Couldn't load image: textures/black
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
Opening IP socket: localhost:27666
found DLL in pak file: /home/paul/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/paul/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 3060.66 MHz
Compiled 'weapon_machinegun::Lower': 1807.0 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67875, 1357500 bytes
   Functions: 2109, 250532 bytes
   Variables: 147376 bytes
    Mem used: 2479288 bytes
 Static data: 2277552 bytes
   Allocated: 3284544 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
WARNING: Couldn't load image: textures/sfx/monitor_glass2
session initialized
--------------------------------------
--- Common Initialization Complete ---
------------- Warnings ---------------
during DOOM 3 initialization...
WARNING: Couldn't load image: textures/black
WARNING: Couldn't load image: textures/sfx/monitor_glass2
2 warnings

Type 'help' for dedicated server info.

terminal support enabled ( use +set in_tty 0 to disabled )
pid: 2231
1008 MB System Memory
Async thread started

---

