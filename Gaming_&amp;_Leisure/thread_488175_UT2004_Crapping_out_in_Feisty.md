---
title: "UT2004 Crapping out in Feisty"
date: 2007-06-29
forum: Gaming &amp; Leisure
---

### Post by lingenfr on 2007-06-29
It runs fine and then just disappears. No error. Nothing. UT2004.log says:

Log: Log file open, Fri Jun 29 21:38:06 2007
Init: Name subsystem initialized
Init: Version: 3369 (128.29)
Init: Compiled: Dec 16 2005 13:23:47
Init: Command line: 
Init: (This is Linux patch version 3369.2)
Init: Character set: Unicode
Init: Base directory: /home/lingenfr/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2005-11-23_16.22]
Init: Object subsystem initialized
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 5.866454...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NvidiaLogo.ut2?Name=Ling_On_Linux?Class=Engine.Pawn?Character=Jakob?team=255
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 33859->33856; refs: 350205
Log: Game class is 'CinematicGame'
Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 7.071134...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Log: ALAudio: Using ALC_EXT_capture to record audio.
ScriptLog: New Player Ling_On_Linux id=af002b1f4c2dffc593d3f3e096b0bf33
Log: TTS: No output filename specified.
Log: Enter SetRes: 1280x1024 Fullscreen 1
Log: OpenGL
Log: GL_VENDOR     : ATI Technologies Inc.
Log: GL_RENDERER   : ATI Radeon 9550 / X1050 Series
Log: GL_VERSION    : 2.0.6473 (8.37.6)
Log: OpenGL: Device supports: GL
Log: OpenGL: Device supports: GL_EXT_bgra
Log: OpenGL: Device supports: GL_ARB_texture_compression
Log: OpenGL: Device supports: GL_EXT_texture_compression_s3tc
Log: OpenGL: Device supports: GL_ARB_texture_cube_map
Log: OpenGL: Device supports: GL_ARB_texture_env_combine
Log: OpenGL: Device supports: GL_ATIX_texture_env_combine3
Log: OpenGL: Device supports: GL_ATI_texture_env_combine3
Log: OpenGL: Device supports: GL_ARB_texture_env_crossbar
Log: OpenGL: Device supports: GL_EXT_texture_lod_bias
Log: OpenGL: Device supports: GL_ARB_multitexture
Log: OpenGL: Device supports: GL_ATI_vertex_array_object
Log: OpenGL: Device supports: GL_ATI_element_array
Log: OpenGL: Device supports: GL_ATI_map_object_buffer
Log: OpenGL: Device supports: GL_ARB_multisample
Log: OpenGL: Device supports: GL_EXT_texture_filter_anisotropic
Log: OpenGL: Device supports: GL_ARB_vertex_buffer_object
Log: OpenGL: Device supports: GL_ARB_fragment_program
Log: OpenGL: Device supports: GL_ARB_vertex_program
Log: OpenGL: Device supports: GL_EXT_framebuffer_object
Log: OpenGL: C32 RGB888 Z24 S0
Log: OpenGL: Level of anisotropy is 1.000000 (max 16.000000).
Log: OpenGL: Have 0 multisamples buffers, 0 samples.
Log: OpenGL: Failed to get a multisample GL context
Log: OpenGL: Forcibly disabled pixel shaders.
Log: OpenGL: Forcibly disabled render-to-texture.
Log: Startup time: 8.118584 seconds
Log: Precaching: NvidiaLogo.LevelInfo0
Log: Static mesh batches: 508608 vertex bytes, 110460 index bytes
Log: Allocating 32768 byte dynamic index buffer.
Log: Allocating 65536 byte dynamic vertex buffer.
Log: Finished precaching geometry in 0.032 seconds
Log: Finished precaching textures in 0.264 seconds
Debug: UT2k4MainMenu.Opened()   Sender:Package.UT2k4MainMenu
Log: URL: Adding default option Name=Ling_On_Linux
Log: URL: Adding default option Class=Engine.Pawn
Log: URL: Adding default option Character=Jakob
Log: URL: Adding default option team=255
Log: Browse: Index.ut2?disconnect?Name=Ling_On_Linux?Class=Engine.Pawn?Character=Jakob?team=255
Log: Failed; returning to Entry
ScriptLog: UT2k4MainMenu NotifyLevelChange  PendingConnection:False
Log: GP=FALSE
Log: Spawning new actor for Viewport SDLViewport
ScriptLog: New Player Ling_On_Linux id=af002b1f4c2dffc593d3f3e096b0bf33
Log: Static mesh batches: 0 vertex bytes, 0 index bytes
IRC: 2 Servers 0 Channels
Log: Defaulting to false
Log: gethostbyname failed (ETIMEDOUT) ... can't get local IP.
ScriptLog: UT2k4Browser_ServerListPageFavorites Spawned new ServerQueryClient 'Entry.ServerQueryClient'
Log: Defaulting to false
Log: gethostbyname failed (ETIMEDOUT) ... can't get local IP.
Log: Resolving ut2004master1.epicgames.com...
Log: Resolved ut2004master1.epicgames.com -> 216.27.56.6
Log: gethostbyname failed (ETIMEDOUT) ... can't get local IP.
Log: Connection established.
Log: Allocating 184176 byte dynamic vertex buffer.
Log: Resolving ut2004master2.epicgames.com...
Log: Allocating 185904 byte dynamic vertex buffer.
Log: Resolved ut2004master2.epicgames.com -> 216.27.56.6
Log: gethostbyname failed (ETIMEDOUT) ... can't get local IP.
Log: Connection established.
Log: RecvFrom returned SOCKET_ERROR 111
Log: RecvFrom returned SOCKET_ERROR 111
Log: RecvFrom returned SOCKET_ERROR 111
Log: RecvFrom returned SOCKET_ERROR 111
Log: SendTo: 85.25.130.162:8889 returned -1: 111
Log: RecvFrom returned SOCKET_ERROR 111
Log: RecvFrom returned SOCKET_ERROR 111
Log: RecvFrom returned SOCKET_ERROR 111
Debug: UT2k4MainMenu.Opened()   Sender:None
ScriptLog: PreClientTravel
Log: URL: Adding default option Name=Ling_On_Linux
Log: URL: Adding default option Class=Engine.Pawn
Log: URL: Adding default option Character=Jakob
Log: URL: Adding default option team=255
Log: Browse: 63.211.105.170/Index.ut2?Name=Ling_On_Linux?Class=Engine.Pawn?Character=Jakob?team=255
Log: gethostbyname failed (ETIMEDOUT) ... can't get local IP.
Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.PS_Cube
Warning: Missing TexEnvMap TexEnvMap AW-Cubes.Cubes.SunC
Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.MesaEnv2
ScriptLog: UT2k4Browser_ServerListPageFavorites Destroying ServerQueryClient 'ServerQueryClient'
Log: NetMode now NM_Client
Log: Collecting garbage
Log: Purging garbage
Log: (Karma): Level Karma Terminated.
Log: Garbage: objects: 58103->57244; refs: 791681
Log: Bringing Level ONS-Torlan-PhoenixParadise-RMD.myLevel up for play (90) appSeconds: 51.547783...
Log: Spawning new actor for Viewport SDLViewport
ScriptLog: New Player Ling_On_Linux id=af002b1f4c2dffc593d3f3e096b0bf33
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 58350->58350; refs: 804783
Log: AntiTCCSecurePlayer setplayer SDLViewport
Log: Precaching: ONS-Torlan-PhoenixParadise-RMD.LevelInfo0
Log: Static mesh batches: 9734652 vertex bytes, 939954 index bytes
Log: Allocating 32768 byte dynamic index buffer.
Log: Allocating 182508 byte dynamic index buffer.
Log: Preprocessing:  Vertex stream total vertices: 180 Orig wedges: 180
Log: Allocating 65536 byte dynamic vertex buffer.
Log: Preprocessing:  Vertex stream total vertices: 86 Orig wedges: 86
Log: Finished precaching geometry in 2.110 seconds
Log: Finished precaching textures in 4.003 seconds
Log: AttachToBone: No bone named [Bone_Flash] found in actor baSBioAttachment's skeleton.
Log: Opening user log ../UserLogs/AntiTCC_ClientConsoleLog.log
AntiTCC:  
AntiTCC: ==================================================
AntiTCC:  Anti TCC v1.18j build 2005-11-08 12:56
AntiTCC:  Copyright (c) 2003-2005 Wormbo
AntiTCC: ==================================================
AntiTCC:  
AntiTCC:  * Welcome on [un]RealMassDestruction
AntiTCC:  * Your unique ID is [ af002b1f-4c2dffc5-93d3f3e0-96b0bf33 ]
AntiTCC:  * Player ID logging is enabled
AntiTCC:  * Check Timeout: 60 seconds
AntiTCC:  * Reaction to insecurities: SessionBan
AntiTCC:  * Reaction to blacklisted files and classes: SessionBan
AntiTCC:  * Reaction to modified skins: Kick
AntiTCC:  * Reaction to invalid render settings: Message
AntiTCC:  * Reaction to Temporary Console commands: Kick
AntiTCC:  * Anti TCC is running in single MD5 mode
AntiTCC:  * Admins may log in silently
Log: Allocating 94752 byte dynamic vertex buffer.
AntiTCC:  * Verified AntiTCC118j (default)
AntiTCC:  * Verified HumanMaleA (default)
AntiTCC:  * Verified HumanFemaleA (default)
AntiTCC:  * Verified Jugg (default)
AntiTCC:  * Verified Aliens (default)
AntiTCC:  * Verified Bot (default)
AntiTCC:  * Verified SkaarjAnims (default)
AntiTCC:  * Verified XanRobots (default)
AntiTCC:  * Verified ThunderCrash (default)
AntiTCC:  * Verified Hellions (default)
AntiTCC:  * Verified NewNightmare (default)
AntiTCC:  * Verified PlayerSkins (default)
AntiTCC:  * Verified UT2004PlayerSkins (default)
AntiTCC:  * Verified DemoPlayerSkins (default)
AntiTCC:  * Verified BrightPlayerSkins (default)
AntiTCC:  * Verifying skins...
Log: Opening user log ../UserLogs/AntiTCC_ClientConsoleLog.log
AntiTCC:  * Verifying classes...
Log: Opening user log ../UserLogs/AntiTCC_ClientConsoleLog.log
AntiTCC: You have been validated successfully.
Log: 
Developer Backtrace:
Log: [ 1]  ./ut2004-bin [0x874bdd9]
Log: [ 2]  [0xffffe420]
Log: [ 3]  ./ut2004-bin(_ZN16UParticleEmitter13SpawnParticleEifiiRK7FVector+0x62ec) [0x83a009c]
Log: [ 4]  ./ut2004-bin(_ZN16UParticleEmitter14SpawnParticlesEfff+0x196) [0x83a2486]
Log: [ 5]  ./ut2004-bin(_ZN16UParticleEmitter15UpdateParticlesEf+0x37bd) [0x83a5d8d]
Log: [ 6]  ./ut2004-bin(_ZN14USpriteEmitter15UpdateParticlesEf+0x3c) [0x84b873c]
Log: [ 7]  ./ut2004-bin(_ZN8AEmitter4TickEf10ELevelTick+0xbc5) [0x83aec35]
Log: [ 8]  ./ut2004-bin(_ZN6ULevel4TickE10ELevelTickf+0x792) [0x832d302]
Log: [ 9]  ./ut2004-bin(_ZN11UGameEngine4TickEf+0x28e) [0x82dfb2e]
Log: [10]  ./ut2004-bin(_ZN9CMainLoop7RunLoopEv+0xfc) [0x816facc]
Log: [11]  ./ut2004-bin [0x8165646]
Log: [12]  ./ut2004-bin(main+0x3708) [0x8160e08]
Log: [13]  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d2bebc]
Log: [14]  ./ut2004-bin(readdir+0x91) [0x815d4b1]
Log: Unreal Call Stack: UParticleEmitter::SpawnParticle <- UParticleEmitter::SpawnParticles <- USpriteEmitter::UpdateParticles <- AEmitter::Tick <- TickAllActors <- ULevel::Tick <- TickLevel <- UGameEngine::Tick <- UpdateWorld <- MainLoop
Exit: Exiting.
Log: FileManager: Reading 0 GByte 102 MByte 241 KByte 652 Bytes from HD took 15.830242 seconds (15.830242 reading, 0.000000 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Allocation checking disabled
Uninitialized: Log file closed, Fri Jun 29 21:40:57 2007

I don't see any errors. Any ideas?

---

### Post by lingenfr on 2007-06-30
I thought that I had seen something about upgrading SDL, but 1.2 is in the repository. You can go to the website and get 1.2 or 1.3 from svn. Come on, how about some help.

---

