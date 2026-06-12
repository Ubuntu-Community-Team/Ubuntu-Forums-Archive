---
title: "Jedi Academy"
date: 2006-07-30
forum: Gaming &amp; Leisure
---

### Post by thunderduck3141 on 2006-07-30
i just installed Jedi Academy via the loki installer and all went just dandy, now i try to run:

JA: v1.0.1.0 win-x86 Oct 24 2003
Initialising zone memory .....
----- FS_Startup -----
Current search path:
Z:\usr\local\games\jediacademy\base\assets3.pk3 (16 files)
Z:\usr\local\games\jediacademy\base\assets2.pk3 (62 files)
Z:\usr\local\games\jediacademy\base\assets1.pk3 (8320 files)
Z:\usr\local\games\jediacademy\base\assets0.pk3 (15346 files)
Z:\usr\local\games\jediacademy/base

----------------------
23744 files in pk3 files
execing default.cfg
couldn't exec jaconfig.cfg
couldn't exec autoexec.cfg
...detecting CPU, found AMD w/ 3DNow!

------- Input Initialization -------
Skipping check for DirectInput
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
--- Common Initialization Complete ---
Working directory: Z:\usr\local\games\jediacademy
Initializing OpenGL subsystem
...initializing QGL
succeeded
...setting mode 4: 800 600 FS
...using desktop display depth of 24
...calling CDS: ok
...registered window class
...created window@0,0 (800x600)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 24, 24, 8 )
...-1 PFDs found
...GLW_ChoosePFD failed
...GLW_ChoosePFD( 24, 24, 0 )
...-1 PFDs found
...GLW_ChoosePFD failed
...failed to find an appropriate PIXELFORMAT
...restoring display settings
...WARNING: could not set the given mode (4)
...setting mode 3: 640 480 FS
...using colorsbits of 16
...calling CDS: ok
...created window@0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 16, 16, 0 )
...-1 PFDs found
...GLW_ChoosePFD failed
...GLW_ChoosePFD( 16, 16, 0 )
...-1 PFDs found
...GLW_ChoosePFD failed
...failed to find an appropriate PIXELFORMAT
...restoring display settings
...WARNING: could not set the given mode (3)
...shutting down QGL
...unloading OpenGL DLL
----- CL_Shutdown -----
-----------------------
GLW_StartOpenGL() - could not load OpenGL subsystem






any ideas?

---

### Post by Footissimo on 2006-07-30
Other OpenGL games working OK I presume?  The installer still requires Wine to be installed, yeah?  I get Jedi Academy working best on Wine v 0.9.16

I cheated a bit with Jedi Academy and installed it on Windows, put the no CD patch on then copy and pasted it to the .wine directory.  Works lovely that way.

---

### Post by thunderduck3141 on 2006-07-30
now that i check it, none work (new ubuntu install plus newest wine) all 3d games complain the same way, i hope this isnt regression, i guess ill try a new install and compile .17 again and give it a wirl

---

### Post by Footissimo on 2006-07-30
.9.18 is around now.  I had problems with cursor / mouse movement and .9.17 - hence the use of a previous version.

Oh well, good luck :)

---

### Post by thunderduck3141 on 2006-08-01
well, i got it working now w/o difficulty, used loki installer, but i get no character models! some one help

---

### Post by mostwanted on 2006-08-03
> **thunderduck3141 said:**
> now that i check it, none work (new ubuntu install plus newest wine) all 3d games complain the same way, i hope this isnt regression, i guess ill try a new install and compile .17 again and give it a wirl

You need to install 3D drivers.

---

### Post by thunderduck3141 on 2006-08-03
no, well sorta...
yeah i had nvida enabled, but didnt comment out "dri" in xorg.conf
once i did
boom it works
weird:confused:

---

