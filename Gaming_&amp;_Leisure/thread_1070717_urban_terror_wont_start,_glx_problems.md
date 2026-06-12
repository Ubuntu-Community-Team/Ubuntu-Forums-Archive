---
title: "urban terror wont start, glx problems?"
date: 2009-02-15
forum: Gaming &amp; Leisure
---

### Post by anliveyak on 2009-02-15
i have benn playing urban terror for a while now and never had any major problems. i think it was after an update that this happened. when i try to start urban terror i get this console output,
```
ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
13050 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```
i have reinstalled glx-new, and glx and just about everything and cant fix it. also some of my media players and wine arent working.
any ideas or help is greatly appreciated.

---

### Post by johnjohn2 on 2009-02-17
Working here with fglrx

Youon ATI?

---

### Post by anliveyak on 2009-02-17
no, nvidia

---

### Post by tagger on 2009-11-09
I was getting the same problem, I discovered for me it was an in game variable that was set out of range for my video card.

The variable "r_depthbits" needs to be set to a range between 0 and 24 (24 should work for most systems). I detailed my error, and how to fix it on my site [http://urt.taggedzi.com/erdepth.php]("http://urt.taggedzi.com/erdepth.php") 

An alternative option for you is to set your screen resolution to higher than 1024x768 (in urban terror or most ioquake3 game mods) this is r_mode 6. This worked in my system however I think it is a hack work around as the real problem is the depthbits.

Hope this helps some players out there.

---

### Post by magog45 on 2009-12-08
> **tagger said:**
> I was getting the same problem, I discovered for me it was an in game variable that was set out of range for my video card.

The variable "r_depthbits" needs to be set to a range between 0 and 24 (24 should work for most systems). I detailed my error, and how to fix it on my site [http://urt.taggedzi.com/erdepth.php]("http://urt.taggedzi.com/erdepth.php") 

An alternative option for you is to set your screen resolution to higher than 1024x768 (in urban terror or most ioquake3 game mods) this is r_mode 6. This worked in my system however I think it is a hack work around as the real problem is the depthbits.

Hope this helps some players out there.

Exactly which file gets the modification, I couldn't find anything that looked like that in the config files

---

### Post by 5nak3 on 2009-12-08
if i'm not mistaken these are the files you would need to look at

execing default.cfg
execing q3config.cfg
execing autoexec.cfg


most likely the default or q3config as opposed to the autoexec. Best thing to do is use ctrl+f to find the command you need to edit.

---

