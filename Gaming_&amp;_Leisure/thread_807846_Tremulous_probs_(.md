---
title: "Tremulous probs :("
date: 2008-05-26
forum: Gaming &amp; Leisure
---

### Post by hungryOrb on 2008-05-26
hihi!
Installed Tremulous (not long after a fresh install of Ubuntu) but, the screen only flashes partly black, and then normal again and nothing else seems to happen!
Is there some prereq software I need that wasn't on the synaptic list?
hmmmm. 
Any help is cool ;D
Thanks for considering ::::]
Orb

---

### Post by hungryOrb on 2008-05-26
This is what I get in my terminal:

```
tremulous
tremulous 1.1.0 linux-x86 Jun 16 2007
----- FS_Startup -----
Current search path:
/home/gen/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
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
```

Hmm.. Does this mean my 3dcard (laptop nvidia 8400) is not working atm? Not got it installed properly?

Thanks for considering :]

---

### Post by Perfect Storm on 2008-05-26
Did you installed the nvidia restriction driver?

---

### Post by hungryOrb on 2008-05-26
> **Artificial Intelligence said:**
> Did you installed the nvidia restriction driver?

No I didn't ;p But erm, on this laptop, I never had the 'pop-up choice' therefore I assumed that all was installed correctly. :/

---

### Post by LeoSolaris on 2008-05-26
It's under Computer->Administration->Hardware Drivers. Just check the box, and let it do the rest, then restart when it says to.

Leo

---

### Post by hungryOrb on 2008-05-27
> **LeoSolaris said:**
> It's under Computer->Administration->Hardware Drivers. Just check the box, and let it do the rest, then restart when it says to.

Leo

Thankyou Leo!

---

### Post by LeoSolaris on 2008-05-28
Na, that one was the Mod's idea, I just responded to your no because he wasn't online.

---

### Post by drksolo12 on 2008-06-07
im having the exact same prob lol i only got ubuntu less that 12 hours ago so im still a little new plus im  not good with computers but could you tell me how to fix this problem?

---

