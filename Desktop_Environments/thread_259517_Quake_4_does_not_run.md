---
title: "Quake 4 does not run"
date: 2006-09-17
forum: Desktop Environments
---

### Post by chevett on 2006-09-17
Hello everyone, thanks for reading this. This is the first time I have tried to get a game going on ubuntu and it is not going well.  Also, I am rather new to linux.

I followed instructions from here [http://www.lucentplum.com/?p=16]("http://www.lucentplum.com/?p=16") even though I'm running Dapper Drake.  The install went fine.

Then I tried to run the game.  I opened a terminal and typed 'sudo quake4'.  Here is the tail end of the output of that:

--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 1024x768 1024x768 960x600 840x525
840x525 832x624 800x600 800x600 800x600 800x600 720x450 700x525 700x525 640x480
640x512 640x512 640x480 640x480 640x480 640x400 640x384 576x432 512x384 512x384
512x384 416x312 400x300 400x300 400x300 320x240 320x240 320x240
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x1024 1280x960 1280x800 1280x768 1152x864 1024x768 1024x768 1024x768 960x600 840x525
840x525 832x624 800x600 800x600 800x600 800x600 720x450 700x525 700x525 640x480
640x512 640x512 640x480 640x480 640x480 640x400 640x384 576x432 512x384 512x384
512x384 416x312 400x300 400x300 400x300 320x240 320x240 320x240
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL


So, then I also tried killing gnome and running quake4 from just a prompt.  When I do this I think quake4 is actually starting, but my monitor prints a message like "The signal is out of Range. Must be below 1024x980." or something like that.  

Then I tried "sudo quake4 set+ r_mode 4 set+ r_displayRefresh" and it doesn't make a difference at all.  I still get the exact same signal out of range message.

Does anyone have any ideas?  I still think it is just a resolution problem, but I could be way off.  I'm out of ideas on how to fix this.  Any help would be great.  Thanks a lot.

---

### Post by chevett on 2006-09-17
in the above post
"sudo quake4 set+ r_mode 4 set+ r_displayRefresh"

should be
"sudo quake4 set+ r_mode 4 set+ r_displayRefresh 60"

this doesn't fix anything though.

---

### Post by chevett on 2006-09-17
I realized that my nvidia was not setup.

"sudo nvidia-glx-config enable" fixed it.

I also installed the package ia32-libs-sdl because the package description says "Commercial games like Quake4 are known to work with this package installed".

Now here is the error I am getting when I am trying to run from within gnome.
 Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Jul 21 2006
83ms to load 117k of entityDef
0ms to load 0k of articulatedFigure
Initializing event system
...531 event definitions
Initializing class hierarchy
...247 classes, 598968 bytes for event callbacks
Initializing scripts
TODO: Sys_SetClipboardData
------------ Game Map Shutdown --------------
---------------------------------------------
********************
ERROR: Couldn't load scripts/main.script

********************
Sys_Error: Error during initialization


At the prompt I am still getting the "Signal out of range error"

Also, I forgot to mention this is for an amd64.

---

