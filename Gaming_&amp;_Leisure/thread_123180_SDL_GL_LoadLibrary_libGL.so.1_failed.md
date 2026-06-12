---
title: "SDL_GL_LoadLibrary libGL.so.1 failed ?"
date: 2006-01-29
forum: Gaming &amp; Leisure
---

### Post by _jB on 2006-01-29
Hello :)
I've had this problem for a while now, and I'm kinda getting tired of it :-k
I can run UT2004 (demo), Quake3 a.s.o without any problems, but quake4 and anything releated to SDL failes :cry:

**1**; _Quake4_
> --------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
TODO: Sys_SetClipboardData
********************
ERROR: SDL_GL_LoadLibrary libGL.so.1 failed: No dynamic GL support in video driver

********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_GL_LoadLibrary libGL.so.1 failed: No dynamic GL support in video driver I've triede installing SDL from source, throug apt-get a.s.o but nothing seem to work. Also tried misc. stuff like **LD_PRELOAD=libGL.so.1 quake4**, **quake4 +set snd_driver oss** (or similar) a.s.o, all fail :\

**2**; [U]Half Life 2
[/U]I've gotten steam and hl2 installed, and it runs "fine" (well, steam does). But hl2 will only run i software-mode, wich isn't any good
> **hl2.sh**
cd "/home/jb/Desktop/wine/Program Files/Steam"
wine Steam.exe -opengl -fullscreen -applaunch 220 -dxlevel 81 -novid -console -heapsize 512000 -map_background none & 
My libGL's are like this
> **jb@ubu:/usr/lib$**
-rw-r--r--  1 root 619288 2006-01-28 22:52 libGL.a
lrwxrwxrwx  1 root     10 2006-01-28 22:52 libGL.so -> libGL.so.1
lrwxrwxrwx  1 root     12 2006-01-20 06:38 libGL.so.1 -> libGL.so.1.2
lrwxrwxrwx  1 root     25 2006-01-20 06:38 libGL.so.1.2 -> ../X11R6/lib/libGL.so.1.2
-rw-r--r--  1 root 667994 2006-01-28 22:52 libGLU.a
lrwxrwxrwx  1 root     11 2006-01-28 22:52 libGLU.so -> libGLU.so.1
lrwxrwxrwx  1 root     20 2005-12-01 15:00 libGLU.so.1 -> libGLU.so.1.3.060302
-rw-r--r--  1 root 483084 2005-12-01 15:00 libGLU.so.1.3.060302

**jb@ubu:/usr/local/sbin$**
-rw-r--r--   1 root 634628 2006-01-02 18:17 libGL.so.1 
Anyone have an idea how to fix this ? Tired of playing UT instead of Q4 \\:D/

---

### Post by _jB on 2006-02-02
**no ?**

bummer :\

---

