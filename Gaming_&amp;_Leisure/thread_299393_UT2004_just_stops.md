---
title: "UT2004 just stops"
date: 2006-11-14
forum: Gaming &amp; Leisure
---

### Post by silwerspawn on 2006-11-14
Hello everyone!

I'm having a bit trouble with my UT2004.
When I start it i can see the intro, but when its going to jump into the menu it quits, it gives me an warning but i have read that is doesn't matter. Please tell me what I'm doing wrong!](*,)

---

### Post by livingtarget on 2006-11-14
Poking around in /home/YOUR_USERNAME/.ut2004/System/ut2004.log may give you more clues as to what is going on. This is usually where you will find a bit more information.

If possible "attach" it to your post.

---

### Post by silwerspawn on 2006-11-14
Here is the log file. 

Log: Log file open, Tue Nov 14 11:30:10 2006
Init: Name subsystem initialized
Init: Version: 3355 (128.29)
Init: Compiled: Feb 20 2005 03:38:34
Init: Command line: 
Init: (This is Linux patch version 3355.0)
Init: Character set: Unicode
Init: Base directory: /usr/local/games/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2005-02-15_17.02]
Init: Object subsystem initialized
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 4.806953...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NvidiaLogo.ut2?Name=Player?Class=Engine.Pawn?Character=Jakob?team=255
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 33837->33834; refs: 349964
Log: Game class is 'CinematicGame'
Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 6.003082...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Log: ALAudio: Using ALC_EXT_capture to record audio.
ScriptLog: New Player Player id=01119a6f291a5921605cda14071ba772
Log: TTS: No output filename specified.
Log: Enter SetRes: 800x600 Fullscreen 1
Log: OpenGL
Log: GL_VENDOR     : Tungsten Graphics, Inc.
Log: GL_RENDERER   : Mesa DRI Radeon 20060327 AGP 4x NO-TCL
Log: GL_VERSION    : 1.3 Mesa 6.5.1
Log: OpenGL: Device supports: GL
Log: OpenGL: Device supports: GL_EXT_bgra
Log: OpenGL: Device supports: GL_ARB_texture_compression
Log: OpenGL: Device supports: GL_ARB_texture_cube_map
Log: OpenGL: Device supports: GL_ARB_texture_env_combine
Log: OpenGL: Device supports: GL_ATI_texture_env_combine3
Log: OpenGL: Device supports: GL_ARB_texture_env_crossbar
Log: OpenGL: Device supports: GL_EXT_texture_lod_bias
Log: OpenGL: Device supports: GL_ARB_multitexture
Log: OpenGL: Device supports: GL_ARB_multisample
Log: OpenGL: Device supports: GL_EXT_texture_filter_anisotropic
Log: OpenGL: C32 RGB888 Z24 S0
Log: OpenGL: Level of anisotropy is 1.000000 (max 16.000000).
Log: OpenGL: Have 0 multisamples buffers, 0 samples.
Log: OpenGL: Failed to get a multisample GL context
Log: WARNING: OpenGL renderer relies on DXTC/S3TC support for good performance.
Log: Startup time: 6.725737 seconds
Log: Precaching: NvidiaLogo.LevelInfo0
Log: Static mesh batches: 508608 vertex bytes, 110460 index bytes
Log: Allocating 32768 byte dynamic index buffer.
Log: Allocating 65536 byte dynamic vertex buffer.
Log: Finished precaching geometry in 0.071 seconds
Log: Finished precaching textures in 0.392 seconds
Debug: UT2k4MainMenu.Opened()   Sender:Package.UT2k4MainMenu
Log: URL: Adding default option Name=Player
Log: URL: Adding default option Class=Engine.Pawn
Log: URL: Adding default option Character=Jakob
Log: URL: Adding default option team=255
Log: Browse: Index.ut2?disconnect?Name=Player?Class=Engine.Pawn?Character=Jakob?team=255
Log: Failed; returning to Entry
ScriptLog: UT2k4MainMenu NotifyLevelChange  PendingConnection:False
Log: GP=FALSE
Log: Spawning new actor for Viewport SDLViewport
ScriptLog: New Player Player id=01119a6f291a5921605cda14071ba772
Log: Static mesh batches: 0 vertex bytes, 0 index bytes
Log: Log file closed, Tue Nov 14 11:30:22 2006

---

### Post by livingtarget on 2006-11-14
Odd, ut2004 seems to be alright except that it just quits. 

Try this: hit the ` or the ~ key to open the console. This depends on your keyboard I think. Once in the console type:

open dm-rankin

That should load dm-rankin, if that works then it's just a weird bug where it crashes where it hits the menu. If that's the case then I suspect it may be your video drivers.

The log looks identical to mine, except it just quits before the main menu entry.

You should also try to patch it to the latest version if possible. I see you use 3355, the latest patch is 3369.

Hope that helps.

---

