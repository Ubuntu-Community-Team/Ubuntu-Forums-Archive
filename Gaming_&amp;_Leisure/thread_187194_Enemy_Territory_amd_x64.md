---
title: "Enemy Territory amd x64"
date: 2006-06-02
forum: Gaming &amp; Leisure
---

### Post by krak on 2006-06-02
Hello, today after long break with linux i have installed Kubuntu 6.06 x64. I have installed ATI drivers and they do work but, et dont.

here whats i get

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/krak/.etwolf/etmain
/home/krak/gry/enemy-territory/etmain/pak2.pk3 (22 files)
/home/krak/gry/enemy-territory/etmain/pak1.pk3 (10 files)
/home/krak/gry/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/krak/gry/enemy-territory/etmain/mp_bin.pk3 (6 files)
/home/krak/gry/enemy-territory/etmain

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
...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libGL.so.1: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by JoWilly on 2006-06-04
I've seen this problem in the past with ET. This also happened on x86.

libGL.so needs to be copied over because ET does not find it.

I think I saw other threads about this same problem.

---

