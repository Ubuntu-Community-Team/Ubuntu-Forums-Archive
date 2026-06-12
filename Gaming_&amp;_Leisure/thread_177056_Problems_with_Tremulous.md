---
title: "Problems with Tremulous"
date: 2006-05-15
forum: Gaming &amp; Leisure
---

### Post by aclaunch on 2006-05-15
I just downloaded the standalone version and it seems to have installed OK. When I go to play the screen blanks, sound comes on and then nothing-no graphics, just the sound playing. Escape. enter etc doesn't work and to quit, I have to log in to another VT and kill the game. Other games seem to work fine.

Dapper latest (5/15/06), PIII 500MHz, 786M RAM, Nvidia cad 32M RAM

Alan

---

### Post by Footissimo on 2006-05-15
What does it say if you try it from a terminal?

Seen another person using Dapper on there (lots of Ubuntu peeps) so I'll ask if he's had any problems when I see him next..

---

### Post by whitey on 2006-05-15
I just installed this game on my laptop, suprisingly it dosen't take much processing power.  Although, the only resolution I can get broadcasts a 2in border around the screen.  I'm going to see if there are updates for the drivers on my video chipset.

Although in bad resolution game runs good.

Laters

---

### Post by aclaunch on 2006-05-15
This is what I get when trying to start from a terminal:

/usr/local/games/tremulous/tremulous.x86 
tremulous 1.1.0 linux-x86 Feb 28 2006
----- FS_Startup -----
Current search path:
/home/aclaunch/.tremulous/base
/usr/local/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/local/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/local/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/local/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/local/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/local/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/local/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/local/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/local/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/local/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/local/games/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
execing autogen.cfg
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
SDL_Init(SDL_INIT_VIDEO) failed: No I/O port permissions
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

It looks like an SDL or OpenGL issue but where do I go from here?

Alan

---

### Post by Footissimo on 2006-05-15
[QUOTE=whitey]I just installed this game on my laptop, suprisingly it dosen't take much processing power.  Although, the only resolution I can get broadcasts a 2in border around the screen.  I'm going to see if there are updates for the drivers on my video chipset.

Although in bad resolution game runs good.

Laters[/QUOTE]

Go into the game - press play and use an empty server.  Once you are in-game, then press Esc->Options->System->GFX Software->Screen size and max it out.

Hopefully that'll sort it :)

aclaunch..obvious question, but do you have the libsdl libraries installed?

---

