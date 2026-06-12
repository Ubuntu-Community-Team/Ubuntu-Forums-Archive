---
title: "Problem running True Combat: Elite"
date: 2006-08-08
forum: Gaming &amp; Leisure
---

### Post by Morbett on 2006-08-08
So I just installed Enemy Territory and then TC: Elite.  I tried to launch TC: Elite and I got the following error:

> ...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...


So I added "+set r_allowSoftwareGL 1" to the end of the command line, which allowed me to launch TC: Elite.  However it's EXTREMELY slow and laggy and I can barely use the menu.

Any idea what I should do?  (I don't have any special graphics card or anything - maybe that's my problem)

Thanks,

---

### Post by Morbett on 2006-08-08
Bump...

I have the same problem when loading Tremulous or Warsow.  I think it's either my hardware or somethine with OpenGL.

> ...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Using 8/8/8 Color bits, 16 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


---

### Post by gurgle on 2006-08-08
my sound isnt working in true combat :/

---

### Post by Morbett on 2006-08-10
Does anyone have any idea how to help my TC : Elite woes?

---

### Post by FindWaldo on 2006-08-10
Does Enemy Territory itself work?

---

### Post by simplyw00x on 2006-08-10
> Any idea what I should do? (I don't have any special graphics card or anything - maybe that's my problem)
If you don't *have* a graphics card then you're unlikely to be able to play any 3D games at all. If, as I suspect is true, you do have a graphics card but haven't installed drivers for it, then post the output of `lspci` and we can work from there.

> my sound isnt working in true combat :/
Try:
```
sudo -s
echo et.x86 0 0 direct > /proc/asound/card0/pcm0p/oss
echo et.x86 0 0 disiable > /proc/asound/card0/pcm0c/oss
```

If this works, add the last 2 lines (echo...) to /etc/environment to make the change permenant.

---

### Post by LordOfKao$ on 2006-08-13
> **Morbett said:**
> So I just installed Enemy Territory and then TC: Elite.  I tried to launch TC: Elite and I got the following error:



So I added "+set r_allowSoftwareGL 1" to the end of the command line, which allowed me to launch TC: Elite.  However it's EXTREMELY slow and laggy and I can barely use the menu.

Any idea what I should do?  (I don't have any special graphics card or anything - maybe that's my problem)

Thanks,

The post above mine is correct (well 99.9% ;) as we don't know for sure) we've seen this many times. If ET cannot detect any form of 3D acceleration, be it a lack of/problem with drivers or the fact 3D acceleration isn't turned on, the r_allowSoftwareGL is the software based mesa OpenGL rendering. As you have found out it is pretty poor performance wise.

---

