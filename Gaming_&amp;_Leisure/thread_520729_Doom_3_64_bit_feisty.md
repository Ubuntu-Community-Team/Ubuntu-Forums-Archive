---
title: "Doom 3 64 bit feisty"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by fain on 2007-08-08
Hello, does any one have doom 3 working in 64 bit ubuntu. I am having trouble getting it to run.
my sys specs are in my sig.
```

DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.4/255.255.255.0
------ Initializing File System ------
Loaded pk4 /mnt/storage/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /mnt/storage/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /mnt/storage/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /mnt/storage/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /mnt/storage/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /mnt/storage/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /mnt/storage/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /mnt/storage/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /mnt/storage/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /mnt/storage/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /mnt/storage/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /mnt/storage/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /mnt/storage/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jay/.doom3/base
/mnt/storage/games/doom3/base
/mnt/storage/games/doom3/base/pak008.pk4 (3 files)
/mnt/storage/games/doom3/base/pak007.pk4 (38 files)
/mnt/storage/games/doom3/base/pak006.pk4 (48 files)
/mnt/storage/games/doom3/base/pak005.pk4 (63 files)
/mnt/storage/games/doom3/base/pak004.pk4 (5137 files)
/mnt/storage/games/doom3/base/pak003.pk4 (4676 files)
/mnt/storage/games/doom3/base/pak002.pk4 (6120 files)
/mnt/storage/games/doom3/base/pak001.pk4 (8972 files)
/mnt/storage/games/doom3/base/pak000.pk4 (2698 files)
/mnt/storage/games/doom3/base/game03.pk4 (2 files)
/mnt/storage/games/doom3/base/game02.pk4 (2 files)
/mnt/storage/games/doom3/base/game01.pk4 (2 files)
/mnt/storage/games/doom3/base/game00.pk4 (2 files)
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
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 38
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 42
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 43
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL
jay@home:~$ sudo doom3
Password:
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.4/255.255.255.0
------ Initializing File System ------
Loaded pk4 /mnt/storage/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /mnt/storage/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /mnt/storage/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /mnt/storage/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /mnt/storage/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /mnt/storage/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /mnt/storage/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /mnt/storage/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /mnt/storage/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /mnt/storage/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /mnt/storage/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /mnt/storage/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /mnt/storage/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jay/.doom3/base
/mnt/storage/games/doom3/base
/mnt/storage/games/doom3/base/pak008.pk4 (3 files)
/mnt/storage/games/doom3/base/pak007.pk4 (38 files)
/mnt/storage/games/doom3/base/pak006.pk4 (48 files)
/mnt/storage/games/doom3/base/pak005.pk4 (63 files)
/mnt/storage/games/doom3/base/pak004.pk4 (5137 files)
/mnt/storage/games/doom3/base/pak003.pk4 (4676 files)
/mnt/storage/games/doom3/base/pak002.pk4 (6120 files)
/mnt/storage/games/doom3/base/pak001.pk4 (8972 files)
/mnt/storage/games/doom3/base/pak000.pk4 (2698 files)
/mnt/storage/games/doom3/base/game03.pk4 (2 files)
/mnt/storage/games/doom3/base/game02.pk4 (2 files)
/mnt/storage/games/doom3/base/game01.pk4 (2 files)
/mnt/storage/games/doom3/base/game00.pk4 (2 files)
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
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 38
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 42
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 43
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL
jay@home:~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.4/255.255.255.0
------ Initializing File System ------
Loaded pk4 /mnt/storage/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /mnt/storage/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /mnt/storage/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /mnt/storage/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /mnt/storage/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /mnt/storage/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /mnt/storage/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /mnt/storage/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /mnt/storage/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /mnt/storage/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /mnt/storage/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /mnt/storage/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /mnt/storage/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jay/.doom3/base
/mnt/storage/games/doom3/base
/mnt/storage/games/doom3/base/pak008.pk4 (3 files)
/mnt/storage/games/doom3/base/pak007.pk4 (38 files)
/mnt/storage/games/doom3/base/pak006.pk4 (48 files)
/mnt/storage/games/doom3/base/pak005.pk4 (63 files)
/mnt/storage/games/doom3/base/pak004.pk4 (5137 files)
/mnt/storage/games/doom3/base/pak003.pk4 (4676 files)
/mnt/storage/games/doom3/base/pak002.pk4 (6120 files)
/mnt/storage/games/doom3/base/pak001.pk4 (8972 files)
/mnt/storage/games/doom3/base/pak000.pk4 (2698 files)
/mnt/storage/games/doom3/base/game03.pk4 (2 files)
/mnt/storage/games/doom3/base/game02.pk4 (2 files)
/mnt/storage/games/doom3/base/game01.pk4 (2 files)
/mnt/storage/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
/proc/cpuinfo CPU frequency: 3000 MHz
guessing video ram ( use +set sys_videoRam to force ) ..
Setup X display connection
found XNVCtrl extension 1.13
Detected
        3.00 GHz CPU
        2016 MB of System memory
        256 MB of Video memory on an optimal video architecture

This system qualifies for High quality!
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 800x600
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 46
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 50
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 52
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL
jay@home:~$ clr
bash: clr: command not found
jay@home:~$ clear

jay@home:~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.4/255.255.255.0
------ Initializing File System ------
Loaded pk4 /mnt/storage/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /mnt/storage/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /mnt/storage/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /mnt/storage/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /mnt/storage/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /mnt/storage/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /mnt/storage/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /mnt/storage/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /mnt/storage/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /mnt/storage/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /mnt/storage/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /mnt/storage/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /mnt/storage/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jay/.doom3/base
/mnt/storage/games/doom3/base
/mnt/storage/games/doom3/base/pak008.pk4 (3 files)
/mnt/storage/games/doom3/base/pak007.pk4 (38 files)
/mnt/storage/games/doom3/base/pak006.pk4 (48 files)
/mnt/storage/games/doom3/base/pak005.pk4 (63 files)
/mnt/storage/games/doom3/base/pak004.pk4 (5137 files)
/mnt/storage/games/doom3/base/pak003.pk4 (4676 files)
/mnt/storage/games/doom3/base/pak002.pk4 (6120 files)
/mnt/storage/games/doom3/base/pak001.pk4 (8972 files)
/mnt/storage/games/doom3/base/pak000.pk4 (2698 files)
/mnt/storage/games/doom3/base/game03.pk4 (2 files)
/mnt/storage/games/doom3/base/game02.pk4 (2 files)
/mnt/storage/games/doom3/base/game01.pk4 (2 files)
/mnt/storage/games/doom3/base/game00.pk4 (2 files)
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
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 38
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 42
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 43
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL

```
it acts as if its going to start but crashes with
Sys_Error: Unable to initialize OpenGL
i tried running as root but still a no go
and pre-loading libgl doesn't work either
i also tried to delete the config.spec file in my home dir
this file is empty do i need to populate this with a config maybe?
well i just tried copying my config files from my windows install but no good.

---

### Post by hikaricore on 2007-08-08
I hate to ask, but is direct rendering enabled on your system?

AKA do you have the proper drivers installed and do other 3d apps/games work?

---

### Post by fain on 2007-08-08
Thanks for replying yes i have direct rendering enabled 
```
glxinfo | grep direct
direct rendering: Yes
```
i run SWG in wine all the time
as well have i had WoW working in the past using gl
nexuiz works great too
so the drivers are working.
ive installed the drivers from the nividia site
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11

---

### Post by Sockerdrickan on 2007-08-08
...wine? I got only one URL for you

[http://zerowing.idsoftware.com:6969/stats.html?info_hash=b221a4dee26cf007dd33cfc7871aa70f6899a213](http://zerowing.idsoftware.com:6969/stats.html?info_hash=b221a4dee26cf007dd33cfc7871aa70f6899a213)

---

### Post by fain on 2007-08-08
Hello Tux0r, no i am using the native linux version. i was just using those games as an example saying the nvidia drivers are working. 
I also have some 32 bit libs installed because of wine but i don't know, maybe i need certain 32 bit libs for doom 3?

---

### Post by Sockerdrickan on 2007-08-08
sudo apt-get install ia32-libs*
try that :popcorn:

---

### Post by fain on 2007-08-08
Nope :confused: guess its not the 32 libs :( 
I had my default color depth set to 16 bit because of a bug in wine and another game i play.
I switched it back to 24 and now it does something different. 
when i start doom3 the screen goes black like it did b4
but now it doesn't do anything, just blackness.
Its not what i wanted but at least i got some where :)
thx for all your guys help

---

### Post by Sockerdrickan on 2007-08-09
I have this problem too, Quake 4 works though, without sound

---

### Post by fain on 2007-08-09
i would hate to go to 32 bit but i just might cause this isn't the first time i've ran into problems with 64bit

---

### Post by fain on 2007-08-09
OMG!!! i found a startup icon in my gnome menu there are 2 doom3 icons for some reason. (edit: ones for the server) i clicked the first one and nothing happened. But the second one started the game!!!! WTF, thats some weird poo there. :guitar:

---

### Post by fain on 2007-08-09
heres whats in my .desktop file that makes it work
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=doom3
Comment=
Exec=/usr/local/games/doom3//doom3
Icon=/usr/local/games/doom3//doom3.png
Terminal=false
Type=Application
Categories=Application;Games;X-Red-Hat-Base;
GenericName[en_US]=

```
not sure why maybe its a bug?
something to do with the terminal=false???
i tried that exact command in a terminal and it did the same thing.

---

### Post by Sockerdrickan on 2007-08-09
Exec=/usr/local/games/doom3//doom3

Sup with the double "/" ?

---

### Post by fain on 2007-08-09
Ya I'm not sure about that. Thats how the doom3 run file installed it.

---

