---
title: "Quake 3 Arena installation"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by daniminas on 2007-03-19
Hi all

I'm looking for some help to install **Quake 3 Arena** in my **Ubuntu Dapper**.. it's the only thing i miss from my Windows installation :confused: 

Thanks!!

---

### Post by SishGupta on 2007-03-19
a simple google search for "quake 3 on linux" gives

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)

as the fourth result

---

### Post by daniminas on 2007-03-25
ok, i been installed it but i'm getting this error([http://pastebin.ca/410111):](http://pastebin.ca/410111):)

```

root@pcdaniel:/usr/local/games/quake3# ./quake3 codered +set r_gldriver libGL.so .1.2
Q3 1.30 linux-i386 Sep 27 2001
----- FS_Startup -----
Current search path:
/root/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4060 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Joystick is not active.
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1.2: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 24 depth, 8 stencil display.
X Error of failed request: BadAlloc (insufficient resources for operation)
  Major opcode of failed request: 143
  Minor opcode of failed request: 3
  Serial number of failed request: 36
X Error of failed request: GLXBadContext
  Major opcode of failed request: 143
  Minor opcode of failed request: 5
  Serial number of failed request: 38
GL_RENDERER: (null)
----- CL_Shutdown -----
RE_Shutdown( 1 )
X Error of failed request: GLXBadContext
  Major opcode of failed request: 143
  Minor opcode of failed request: 4
  Serial number of failed request: 39
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Q_strncpyz: NULL src
root@pcdaniel:/usr/local/games/quake3# 

```

i've a ASRock 775i65g motherboard using the Intel integrated graphics card and it is the 865G chipset. 

Any tips on how to solve this problem?

---

