---
title: "Quake 3"
date: 2008-03-02
forum: Gaming &amp; Leisure
---

### Post by jakl_53 on 2008-03-02
Ive been playing Quake 3 on my computer for a few days now with no problem. But today i go to open it and get this message and Quake doesnt start.
> 
Q3 1.11 win-x86 Nov 24 1999
----- FS_Startup -----
Current search path:
C:\Program Files\Quake III Arena\baseq3\pak0.pk3 (3539 files)
C:\Program Files\Quake III Arena/baseq3

----------------------
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
...detecting CPU, found AMD w/ 3DNow!

------- Input Initialization -------
Initializing DirectInput...
Couldn't set DI coop level
Falling back to Win32 mouse support...
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
--- Common Initialization Complete ---
Winsock Initialized
Opening IP socket: localhost:27960
Hostname: UbuntuSean
IP: 127.0.1.1
WARNING: IPX_Socket: bind: WSAEINVAL
Working directory: C:\Program Files\Quake III Arena
----- R_Init -----
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'c:\windows\system32\opengl32.dll' ): succeeded
...setting mode 3: 640 480 FS
...using desktop display depth of 32
...calling CDS: failed, DISP_CHANGE_FAILED
...trying next higher resolution: failed, DISP_CHANGE_FAILED
...restoring display settings
...registered window class
...created window@3,22 (646x505)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...0 PFDs found
...hardware acceleration found
...PIXELFORMAT 1 selected
...creating GL context: succeeded
...making context current: succeeded
...WARNING: fullscreen unavailable in this mode
...setting mode 3: 640 480 FS
...using colorsbits of 16
...calling CDS: failed, DISP_CHANGE_FAILED
...trying next higher resolution: failed, DISP_CHANGE_FAILED
...restoring display settings
...window already present, CreateWindowEx skipped
Initializing OpenGL driver
...WARNING: fullscreen unavailable in this mode
...shutting down QGL
...unloading OpenGL DLL
...assuming '3dfxvgl' is a standalone driver
...initializing QGL
...WARNING: missing Glide installation, assuming no 3Dfx available
...shutting down QGL
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
GLW_StartOpenGL() - could not load OpenGL subsystem


anyone know whats going on?
and another thing. does anyone know how to get punkbuster working?

---

### Post by Sockerdrickan on 2008-03-03
Are you running 8.04 and just got kernel updates? update again.

---

### Post by jakl_53 on 2008-03-03
and how would i do that? i dont know if i have 8.04. i dont remember an update.

---

### Post by jakl_53 on 2008-03-04
help?

---

### Post by Sockerdrickan on 2008-03-05
```
lsb_release -r
``` :)

---

### Post by King_Critter on 2008-03-05
Are you playing it in Windows? Because at the start of the log there, it says "C:\Program Files\Quake III Arena\baseq3\pak0.pk3 (3539 files)" which is obviously a Windows filesystem. If you'r enot running it in windows, maybe you're acidentally launching it with Wine? o_0

---

### Post by jakl_53 on 2008-03-05
Thanks tux0r. Im still using 7.10.. And i used wine to install it from the cd..

---

### Post by FrozenFox on 2008-03-05
Quake 3 has a native installer. Don't run it in wine.

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)

This may help  you. It's a little longer of a process, but it should work, and better than the original in wine.

---

### Post by disturbedite on 2008-03-05
holy crap, you're running q3 1.11?  thats super ancient!  after q3's source code was released development continued by the community (not ID software) under a slightly different name:
ioquake3
check it out, its great.

and yeah, are you crazy?!  running q3 in wine when there is a native linux version?

---

