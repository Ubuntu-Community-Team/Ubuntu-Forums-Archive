---
title: "Xlib error???"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by stlouis1 on 2007-08-08
well, i just got ut2004 isntalled as root. and it did run.........until i tried to up the resolution

now when i try to run it, i get this

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Couldn't initialize SDL: No available video device




i also get something similar when i try to run doom3 which results in this

----- R_InitOpenGL -----
Setup X display connection
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Couldn't open the X display
Setup X display connection
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Couldn't open the X display
idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL



and i get something similar in quake 4, but i think my issue would be clear by now. i need help

---

### Post by PaulFr on 2007-08-08
One possible cause: Are you switching user using su and then trying to run the commands ? If yes, before switching user, or in a different terminal as the original user that logged in, run the command ```
xhost +local:
``` Then when you switch user, please first run ```
export DISPLAY=:0.0
```Now run your commands and see if they work.

---

### Post by stlouis1 on 2007-08-08
well, i did that, and here's what i got

urmom@urmom-laptop:~$ xhost +local:
non-network local connections being added to access control list

urmom@urmom-laptop:~$ export DISPLAY=:0.0

urmom@urmom-laptop:~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
...............
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


urmom@urmom-laptop:~$ ut2004

WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error




is it safe to say opengl isnt setup right? how do i fix this now

---

### Post by DoktorSeven on 2007-08-08
Almost certainly 3d drivers are not set up.  Try

**glxinfo | grep direct**

If it returns direct rendering: No, then they need to be set up.  For ATi and NVidia cards there's a Restricted Drivers Manager in Feisty (under Administration) that will do the work for you; for other cards or for other versions of Ubuntu, you'll have to search to find out how to enable direct rendering (3d).

---

### Post by stlouis1 on 2007-08-08
i just looked through synaptics and i have nvidia-glx-new and the nvidia-kernel-common packages. and if i go in my nvidia settings panel it says i have a 97.55 version driver installed

though i just checked in the nvidia panel and under the opengl/glx settings it has direct rendering in there too???

---

### Post by stlouis1 on 2007-08-08
well i ran that command it came back with direct rendering: Yes

---

