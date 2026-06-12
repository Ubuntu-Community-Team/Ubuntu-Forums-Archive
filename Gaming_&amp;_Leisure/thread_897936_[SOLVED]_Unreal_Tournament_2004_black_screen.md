---
title: "[SOLVED] Unreal Tournament 2004: black screen"
date: 2008-08-22
forum: Gaming &amp; Leisure
---

### Post by Frem on 2008-08-22
So, I can't get Unreal Tournament 2004 Editor's Choice Edition to work. I've got 3D acceleration via my Intel GMA X3100 card, I've turned off desktop effects, and the game works fine under Windows.

However, when I try to run it under Ubuntu Hardy, it sits there with a black screen and no sound. I was not able to regain control of the system by switching to TTY1, so I was forced to perform a hard reboot. I patched the game to version 3319 (Is this the lastest?); same situation.

I tried linking the system libSDL-1.2.so.0 file to the game one. That showed my cursor stuck in the very center of the screen, but aside from that, same issue.

After a bit of googling, I found [this]("http://icculus.org/~icculus/tmp/please_test_with_ut2004-2.tar.bz2") unofficial test patch and swapped out the .so files. This didn't help any, it's the same as with the system libSDL file.

Here is my ~/.ut2004/System.UT2004.log file. Help!
```
Log: Log file open, Fri Aug 22 14:51:49 2008
Init: Name subsystem initialized
Init: Version: 3319 (128.29)
Init: Compiled: Sep  2 2004 10:07:36
Init: Command line: 
Init: (This is Linux patch version 3319.0)
Init: Character set: Unicode
Init: Base directory: /home/james/games/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2004-09-02_05.02]
Init: Object subsystem initialized
Warning: Missing Class Class Editor.TransBuffer
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 19.241168...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NvidiaLogo.ut2?Name=Player?Class=Engine.Pawn?Character=Jakob?team=255
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 33517->33516; refs: 347743
Log: Game class is 'CinematicGame'
Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 22.321713...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Log: ALAudio: Using ALC_EXT_capture to record audio.
ScriptLog: New Player Player id=83add47e323e9b113250627a8ccd0b2d
Log: TTS: No output filename specified.
Log: Enter SetRes: 800x600 Fullscreen 1
Log: OpenGL
Log: GL_VENDOR     : Tungsten Graphics, Inc
Log: GL_RENDERER   : Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
Log: GL_VERSION    : 1.4 Mesa 7.0.3-rc2
Log: OpenGL: Device supports: GL
Log: OpenGL: Device supports: GL_EXT_bgra
Log: OpenGL: Device supports: GL_ARB_texture_compression
Log: OpenGL: Device supports: GL_EXT_texture_compression_s3tc
Log: OpenGL: Device supports: GL_ARB_texture_cube_map
Log: OpenGL: Device supports: GL_ARB_texture_env_combine
Log: OpenGL: Device supports: GL_ARB_texture_env_crossbar
Log: OpenGL: Device supports: GL_EXT_texture_lod_bias
Log: OpenGL: Device supports: GL_ARB_multitexture
Log: OpenGL: Device supports: GL_ARB_multisample
Log: OpenGL: Device supports: GL_EXT_texture_filter_anisotropic
Log: OpenGL: Device supports: GL_ARB_vertex_buffer_object
Log: OpenGL: C32 RGB888 Z24 S8
Log: OpenGL: Level of anisotropy is 1.000000 (max 2.000000).
Log: OpenGL: Have 0 multisamples buffers, 0 samples.
Log: OpenGL: Failed to get a multisample GL context
Log: WARNING: no support for combine3/4 extensions -> not all blend modes supported
Log: Startup time: 25.829008 seconds
Log: Precaching: NvidiaLogo.LevelInfo0
Log: Static mesh batches: 508608 vertex bytes, 110460 index bytes
Log: Allocating 32768 byte dynamic index buffer.
Log: 
Developer Backtrace:
Log: [ 1]  ./ut2004-bin [0x85aa511]
Log: [ 2]  [0xb7f7a420]
Log: [ 3]  [0xb7f7a410]
Log: [ 4]  /lib/tls/i686/cmov/libc.so.6(gsignal+0x55) [0xb7cd2085]
Log: [ 5]  /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7cd3a01]
Log: [ 6]  /lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb7ccb10e]
Log: [ 7]  /usr/lib/dri/i965_dri.so [0xb3b96a2c]
Log: [ 8]  /usr/lib/dri/i965_dri.so(intel_miptree_image_data+0xed) [0xb3b95d7d]
Log: [ 9]  /usr/lib/dri/i965_dri.so(intel_finalize_mipmap_tree+0x1f2) [0xb3b9dd22]
Log: [10]  /usr/lib/dri/i965_dri.so [0xb3bcf211]
Log: [11]  /usr/lib/dri/i965_dri.so(brw_validate_state+0x261) [0xb3bb9b01]
Log: [12]  /usr/lib/dri/i965_dri.so [0xb3bae055]
Log: [13]  /usr/lib/dri/i965_dri.so(brw_draw_prims+0xa5) [0xb3bae545]
Log: [14]  /usr/lib/dri/i965_dri.so [0xb3c4a594]
Log: [15]  ./ut2004-bin(_ZN22FOpenGLRenderInterface13DrawPrimitiveE14EPrimitiveTypeiiii+0x2dd) [0x870d42d]
Log: [16]  ./ut2004-bin(_ZN12FBspDrawList6RenderEP15FLevelSceneNodeP16FRenderInterface+0xd52) [0x8513aa2]
Log: [17]  ./ut2004-bin(_Z11RenderLevelP15FLevelSceneNodeP16FRenderInterface+0xeb0) [0x83337a0]
Log: [18]  ./ut2004-bin(_ZN15FLevelSceneNode6RenderEP16FRenderInterface+0x66c) [0x831aadc]
Log: [19]  ./ut2004-bin(_ZN16FPlayerSceneNode6RenderEP16FRenderInterface+0x1da) [0x831ee6a]
Log: [20]  ./ut2004-bin(_ZN11UGameEngine4DrawEP9UViewportiPhPi+0x9bb) [0x82408eb]
Log: [21]  ./ut2004-bin(_ZN12USDLViewport7RepaintEi+0x56) [0x86fcb96]
Log: [22]  ./ut2004-bin(_ZN10USDLClient4TickEv+0x159) [0x86fadb9]
```

I tried the UT2004 demo several weeks ago, and it worked OK after some tweaking, but I cannot remember what I did or what tutorial I used.

Edit: Patched to version 3369, no difference.

Edit: Resolved by removing libtxc_dxtn.

---

### Post by FMaz008 on 2009-06-19
Hi, 

I have the exact same problem as you. Screen receive ni signal (black screen) and the sound is playing. I'm also able to quit the game with the keyboard within the menu (Esc + Enter)

I've tried to find a libtxc_dxtn file but I can't find where it is.

I'm using Ubuntu Intrepid...

Operating System: Linux-x86_64
NVIDIA Driver Version: 180.44


I hope your still alive ... with your notification "on" ;)

---

### Post by Frem on 2009-06-19
'Ight

First, the [find]("http://content.hccfl.edu/pollock/Unix/FindCmd.htm") command is your friend.

Second, you've got an Nvidia card. If you're using the proprietary closed source drivers, you shouldn't need to worry about libtxc_dxtn.so; most of the problems related to that affect Intel cards or open source graphics drivers. If you do any gaming at all, I highly recommend not using open source graphics drivers; they're not quite up to snuff at this point.

Third, you *don't* have the same problem. You've got sound playing in the background, something that never initialized for me. This indicates your solution lies elsewhere. Try checking your log files; they should be in /home/yourname/.ut2004/, or someplace thereabouts.

Now, it sounds like the game is just running at a higher resolution than your monitor can support. Go look up how to make the game start at a more reasonable resolution. :-)

Good luck!

---

### Post by FMaz008 on 2009-06-19
1)
Yes, I've used my friend before posting ;) ... I've done a find / -name "libtxc_dxtn*"

2)
Yes I have an NVidia card,
Yes I use the NVidia drivers ( 185.18.14 )

3)
Hum, I see...
Well, I've looked at what you recommended me and found this in the UT2004.ini that seem revelant:
```

[WinDrv.WindowsClient]
WindowedViewportX=640
WindowedViewportY=480
FullscreenViewportX=800
FullscreenViewportY=600
MenuViewportX=640
MenuViewportY=480

[SDLDrv.SDLClient]
WindowedViewportX=640
WindowedViewportY=480
FullscreenViewportX=800
FullscreenViewportY=600
MenuViewportX=640
MenuViewportY=480

StartupFullscreen=True


```



My UT2004.log say:
```

&#28492;&#14951;&#19488;&#26479;&#26144;&#27753;&#8293;&#28783;&#28261;&#8236;&#29254;&#8297;&#30026;&#8302;&#14641;&#12576;&#14904;&#12340;&#12602;&#8244;&#12338;&#14640;&#18698;&#26990;&#14964;&#20000;&#28001;&#8293;&#30067;&#29538;&#29561;&#25972;&#8301;&#28265;&#29801;&#24937;&#26988;&#25978;&#2660;Log: Your locale: [UTF-8].

Log: Enabled UNICODE support.
Init: Version: 3186 (127.29)
Init: Compiled: Mar  3 2004 04:27:14
Init: Command line: 
Init: (This is Linux64 patch version 3186.0)
Init: Character set: Unicode
Init: Base directory: /usr/local/games/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2004-03-03_02.42]
Init: Object subsystem initialized
Warning: Missing Class Class Editor.TransBuffer
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Global MD5: [854dbd3c0f5d2b1bd1be2cc50342e9de]
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 4.676373...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NvidiaLogo.ut2?Name=Player?Class=Engine.Pawn?Character=Jakob?team=255
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 32771->32770; refs: 339562
Log: Game class is 'CinematicGame'
Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 6.470441...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Log: ALAudio: Using ALC_EXT_capture to record audio.
Log: SET PLAYER!
ScriptLog: New Player Player id=651fb1cc06f1e0777a53585b987dcf7b
Log: TTS: No output filename specified.
Log: Enter SetRes: 800x600 Fullscreen 1
Log: OpenGL
Log: GL_VENDOR     : NVIDIA Corporation
Log: GL_RENDERER   : GeForce 7300 GT/PCI/SSE2
Log: GL_VERSION    : 2.1.2 NVIDIA 185.18.14
Log: OpenGL: Device supports: GL
Log: OpenGL: Device supports: GL_EXT_bgra
Log: OpenGL: Device supports: GL_ARB_texture_compression
Log: OpenGL: Device supports: GL_EXT_texture_compression_s3tc
Log: OpenGL: Device supports: GL_ARB_texture_cube_map
Log: OpenGL: Device supports: GL_ARB_texture_env_combine
Log: OpenGL: Device supports: GL_NV_texture_env_combine4
Log: OpenGL: Device supports: GL_EXT_texture_lod_bias
Log: OpenGL: Device supports: GL_ARB_multitexture
Log: OpenGL: Device supports: GL_NV_vertex_array_range
Log: 

```

... yes, it stop with "log:", it's not a bad copy/paste



I've just tried to put the StartupFullscreen to False: The game start just fine !

... I don't want to be picky, but I would prefer fullscreen !


Well, thanks for your help, I'm getting somewhere ! (I'll continue my investigation :) )

---

### Post by Frem on 2009-06-19
Yeah, we can rule libtxc_dxtn out. You don't have it because you don't need it. The functionality is embeded into the Nvidia drivers (you can see this in your log on the line that mentions "GL_EXT_texture_compression_s3tc". If the texture compression library (that's what libtxc_dtxc is) were the issue, the game would have issues in windowed mode also.

Your log seems to indicate that the game is running fine. Which is odd; I've never seen a monitor that couldn't handle 800x600. 

Try going to the games settings menus and setting the resolution to your normal desktop resolution, then activating fullscreen. Does the blackness still happen?

---

### Post by FMaz008 on 2009-06-19
Wooooaaaa !!! like Anakin Skywalker was saying in Starwars Pod Racer: * It's working... It's working !!! *


But it still a bug... I'm not sure where I should repport it ...


Edit:

Thanks !!

---

### Post by Frem on 2009-06-19
Congradulations!

So running at the desktop resolution fixed it?

Check out [this thread]("http://forums.gentoo.org/viewtopic-t-533679-highlight-ut2004+black.html") on the Gentoo forums. It sounds like Xorg is trying to use a higher refresh rate than your monitor supports at low resolutions.

---

