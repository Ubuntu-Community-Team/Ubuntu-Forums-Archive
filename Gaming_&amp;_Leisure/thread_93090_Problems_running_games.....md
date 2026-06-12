---
title: "Problems running games...."
date: 2005-11-21
forum: Gaming &amp; Leisure
---

### Post by nolan- on 2005-11-21
Hi, im a noob please help me !
I have tried to run Doom3, Quake4 and Enemy Territory without luck. I have a San Diego 4000+ 64bit chip and a 7800gtx Nvidia card. I am running 64bit Kubuntu. 
I installed the nvidia drivers through Adept initially and Doom3 worked but nothing else would work. So i followed the guide found here:-
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
And installed the latest 7676 drivers for amd64bit, but now no games work, not even Doom3. 

'sudo sh et'  returns this :-


```

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/nol/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libXxf86vm.so.1: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


```

And 'sudo sh doom3' returns this


```
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.1.64/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/nol/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /home/nol/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /home/nol/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /home/nol/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /home/nol/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /home/nol/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/nol/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/nol/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /home/nol/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/nol/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/nol/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/nol/.doom3/base
/home/nol/doom3/base
/home/nol/doom3/base/pak007.pk4 (38 files)
/home/nol/doom3/base/pak006.pk4 (48 files)
/home/nol/doom3/base/pak005.pk4 (63 files)
/home/nol/doom3/base/pak004.pk4 (5137 files)
/home/nol/doom3/base/pak003.pk4 (4676 files)
/home/nol/doom3/base/pak002.pk4 (6120 files)
/home/nol/doom3/base/pak001.pk4 (8972 files)
/home/nol/doom3/base/pak000.pk4 (2698 files)
/home/nol/doom3/base/game03.pk4 (2 files)
/home/nol/doom3/base/game02.pk4 (2 files)
/home/nol/doom3/base/game01.pk4 (2 files)
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
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
dlopen(libGL.so.1)
idRenderSystem::Shutdown()
signal caught: Segmentation fault
si_code 1
Was in fatal error shutdown: Unable to initialize OpenGL
Trying to exit gracefully..


```

I am guessing that its something to do with my Nvidia driver install?
Is there a way to check it?

Thanks for any help!

NoL

---

### Post by nolan- on 2005-11-23
Hi,
Looks like im not getting much help with this :(
OK now i'm thinking that 32bit OpenGL libraries haven't been installed correctly by the driver, so games can't find them?

I have tried :-
```
mkdir /emul
mkdir /emul/ia32-linux
mkdir /emul/ia32-linux/usr
ln -s /usr/lib32 /emul/ia32-linux/usr/lib
```

But that didn't help.
Is there a way to move this thread to the 64bit forum?
I am beginning to think it belongs there really (might even get some help!) and don't want to cross-post!

Cheers

---

### Post by crane on 2005-11-24
Not real sure myself,
Be sure to check you xorg.conf to make sure it has been configed right. 
Should have the driver set to nvidia not nv and comment out glcore and dri.
Have you restarted xserver after you installed drivers? Not trying to ask stupid questions just thought I'd cover some of the basics.

Just a thought.

---

### Post by nolan- on 2005-11-24
Hi Crane,
Yeah done that mate, no luck.
I'm beginning to think its something to do with my nforce motherboard and the fact that i haven't yet installed the nforce drivers.
Off to work now i'll post here when i finally figure out whats wrong!

---

### Post by crane on 2005-11-24
Just wondering, are you running a 64bit OS. Seems I read somewhere there were still some problems with gaming on 64bit systems.

---

