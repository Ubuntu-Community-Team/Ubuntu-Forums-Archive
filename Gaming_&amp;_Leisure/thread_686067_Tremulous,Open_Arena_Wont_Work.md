---
title: "Tremulous,Open Arena Wont Work"
date: 2008-02-02
forum: Gaming &amp; Leisure
---

### Post by dontgetshocked on 2008-02-02
I have a Nvidia FX 5600 card which has 3d support.

Alien Arena  and Nexuiz run just fine. Graphics support is set to off, i.e. no special effects and no compiz either. I am using Kubuntu 7.10 although the base is Ubuntu , just using the Kubuntu desktop.

Any suggestions?

---

### Post by FrozenFox on 2008-02-03
Edit: Sorry for killing my post there for about 10 minutes, I realized that what I had suggested wouldn't work. hehe. This should though:

Could you please try running them from konsole / the terminal and give us the output? The best way would be:

1) whereis openarena tremulous 

2) run the binary from the results above (in my case, and probably yours, /usr/games/openarena and /usr/games/tremulous) preceded by logsave ~/Desktop/gamename.txt. Of course, replacing gamename with whatever youre running. Repeat for both games. IE:

logsave ~/Desktop/openarena.txt /usr/games/openarena
logsave ~/Desktop/tremulous.txt /usr/games/tremulous

3) Respond to this post with the text files attached or copy n pasted if they're relatively short.

Note: Im running an fx5950, and both of them work fine for me. It may also be helpful to know which nvidia drivers you are using. Open nvidia-settings and you can find this under X Server Information.

---

### Post by danny79m on 2008-02-26
I can't get open arena to work either. This is the log file I created.

Log of /usr/games/openarena 
Tue Feb 26 17:46:04 2008

ioQ3 1.33+oa linux-i386 Jul  5 2007
----- FS_Startup -----
Current search path:
/home/danny/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (96 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (7 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (932 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (187 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (25 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (748 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
1995 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
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
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
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

/usr/games/openarena died with exit status 1

Tue Feb 26 17:46:05 2008
----------------

---

### Post by Crafty Kisses on 2008-02-26
> **danny79m said:**
> I can't get open arena to work either. This is the log file I created.

Log of /usr/games/openarena 
Tue Feb 26 17:46:04 2008

ioQ3 1.33+oa linux-i386 Jul  5 2007
----- FS_Startup -----
Current search path:
/home/danny/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (96 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (7 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (932 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (187 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (25 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (748 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
1995 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
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
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
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

/usr/games/openarena died with exit status 1

Tue Feb 26 17:46:05 2008
----------------

That sounds like your GFX drivers are not installed, post the following output: ```
glxinfo
```

---

