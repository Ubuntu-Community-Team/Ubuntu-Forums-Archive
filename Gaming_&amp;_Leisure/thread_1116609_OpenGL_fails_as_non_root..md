---
title: "OpenGL fails as non root."
date: 2009-04-05
forum: Gaming &amp; Leisure
---

### Post by WitchCraft on 2009-04-05
I've installed all necessary OpenGL drivers.
I can run GL applications fine as long as I run them as root.
as root, glxinfo outputs: direct rendering: yes

as non-root, glxinfo outputs: direct rendering: no

why? Permissions? Group memberships? Both?

> 
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Using 4/4/4 Color bits, 16 depth, 8 stencil display.
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
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


---

### Post by WitchCraft on 2009-06-28
bump.

---

### Post by WitchCraft on 2009-06-29
> **WitchCraft said:**
> bump.

!

---

### Post by FrozenFox on 2009-06-30
What groups are you in?

I remember seeing this problem before, but not how it was solved unfortunately. I suspect it has something to do with groups though, as you might expect.. Are you in the groups 'video' and 'games' and 'users'? You might look in /etc/group and see if there's anything obvious missed.

---

