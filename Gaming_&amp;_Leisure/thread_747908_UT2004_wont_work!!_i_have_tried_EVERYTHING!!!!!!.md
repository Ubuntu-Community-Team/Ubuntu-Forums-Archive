---
title: "UT2004 wont work!! i have tried EVERYTHING!!!!!!"
date: 2008-04-07
forum: Gaming &amp; Leisure
---

### Post by mjp216 on 2008-04-07
Okay, here's the scoop:

I installed UT2004 with instruction in the gaming forum. That worked fine.

Note: It is installed in
> ~/ut2004/
It's executable is:
> ~/ut2004/ut2004

I have 7.10
I have a Intel Mobile Graphics Media Accelerator X3100,
Intel Dual-core T2310 processor (1.46GHz)

When I go to Applications > Games > Unreal Tournament 2004
or
~/ut2004/ut2004
the splash opens and then shortly closes.

i installed the Mega Pack, and the latest patch (3369-2)

when i run it in terminal with or without nonXgl, i get the following:
> mike@mike-laptop:~$ '/home/mike/ut2004/ut2004' 
ReadFile beyond EOF 0+4/0

History: 

Exiting due to error

or
> mike@mike-laptop:~$ nonXgl '/home/mike/ut2004/ut2004' 
non-network local connections being added to access control list
ReadFile beyond EOF 0+4/0

History: 

Exiting due to error


Please help me, i have been searching for a sollution since 6PM... it's 2AM now.
I AM GOING INSANE!!!!!!!!!!!!!!!!!!

---

### Post by Crafty Kisses on 2008-04-07
I've had similar issues, and I resolved them. First before anything, post the following log:
```
~/.ut2004/System/UT2004.log
```

---

### Post by mjp216 on 2008-04-07
okay i ran the log in terminal and i got
> mike@mike-laptop:~$ ~/.ut2004/System/UT2004.log
bash: /home/mike/.ut2004/System/UT2004.log: Permission denied


---

### Post by mjp216 on 2008-04-07
i also tried to run with gedit to see if i can copy the contents and i got 
> &#28492;&#14951;&#19488;&#26479;&#26144;&#27753;&#8293;&#28783;&#28261;&#8236;&#28493;&#8302;&#28737;&#8306;&#14112;&#12320;&#14896;&#13361;&#13114;&#8246;&#12338;&#14384;&#18698;&#26990;&#14964;&#20000;&#28001;&#8293;&#30067;&#29538;&#29561;&#25972;&#8301;&#28265;&#29801;&#24937;&#26988;&#25978;&#2660;Log: Your locale: [UTF-8].

Log: Enabled UNICODE support.
Init: Version: 3186 (127.29)
Init: Compiled: Mar  4 2004 03:07:41
Init: Command line: 
Init: (This is Linux patch version 3186.0)
Init: Character set: Unicode
Init: Base directory: /home/mike/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2004-03-03_02.42]
Init: Object subsystem initialized
Warning: Missing Class Class Editor.TransBuffer
Critical: ReadFile beyond EOF 0+4/0
Exit: Executing UObject::StaticShutdownAfterError
Exit: Exiting.
Log: FileManager: Reading 0 GByte 10 MByte 344 KByte 316 Bytes from HD took 0.218349 seconds (0.058689 reading, 0.159660 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Log file closed, Mon Apr  7 00:14:37 2008

---

### Post by Crafty Kisses on 2008-04-07
> **mjp216 said:**
> i also tried to run with gedit to see if i can copy the contents and i got

Have you tried removing the patch, then try playing it?

---

### Post by mjp216 on 2008-04-07
how would i go of removing the patch?

---

### Post by Crafty Kisses on 2008-04-07
> **mjp216 said:**
> how would i go of removing the patch?

You need to find out where the patch installed first, not sure where it did, and remove it from the folder.

---

### Post by mjp216 on 2008-04-07
well what would it be named?

---

### Post by Perfect Storm on 2008-04-07
I don't think you can remove the patch as it may have replaced some of the older files.


By the way are you running 64-bit?

---

### Post by mjp216 on 2008-04-07
well, maybe i can install a different patch?

---

### Post by mjp216 on 2008-04-07
maybe i should run it in KDE or XFCE???? not that is makes any difference at all, but i am really desperate... and i am upgrading to 8.04 Hardy today... not that it matters either..... i just wanna play ut2004!!!! :(

---

### Post by Crafty Kisses on 2008-04-07
You should update to Hardy and see if there's a difference.

---

### Post by mjp216 on 2008-04-07
yea, i updated hardy and something went really wrong... idk what but lets just say im typing this on my live CD because nothing works anymore. i am so upset! i log  on with gnome and only my desktop and icons show up and none of my applications work.... in a nutshell... im ******!!! wen i log on to gnome i get some error tht says something like something couldnt load MAT, or SAT, or BAT!!!! goddammit somthing with AT at the end! i think!!! IDK what happened i have run out of options, im going to have to reinstall ubuntu... :(
all my work... data... all down the shitter thanks to hardy

---

### Post by mjp216 on 2008-04-07
okay i fixed my major problem with
> dpkg --configure -all
with a restart
i wudnt have been able to do it if i didnt have KDE installed...
so happy i got that fixed

but sadly... UT2004 still wont ******* work!!!!!!!!!!!!!!!!!!

---

### Post by Crafty Kisses on 2008-04-07
Have you tried completely removing UT2004 then reinstalling it without the patch?

---

### Post by mjp216 on 2008-04-07
ive thought about it but, it takes soo damn long, and its not like i can leave it alone, i have to change the cds and stuff. plus, i still have the patch tarball so i could delete the file with the names inside of the game folder but tht might be hazardous to it actually working.

---

### Post by Crafty Kisses on 2008-04-07
Even though it takes awhile it's worth a shot. Some people have complained about the patch causing this issue, but try that, and let me know.

---

### Post by mjp216 on 2008-04-08
okay ill try it later on

---

### Post by PoopyTheJ on 2008-04-14
Same issue here with Gutsy AMD64, my log file is posted below,

Log: Log file open, Mon Apr 14 22:47:29 2008
Init: Name subsystem initialized
Init: Version: 3369 (128.29)
Init: Compiled: Dec 14 2005 17:11:00
Init: Command line: 
Init: (This is Linux64 patch version 3369.2)
Init: Character set: Unicode
Init: Base directory: /usr/local/games/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2005-11-23_16.22]
Init: Object subsystem initialized
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 2.338305...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NvidiaLogo.ut2?Name=PoopyTheJ?Class=Engine.Pawn?Character=Gaargod?team=1?Sex=M
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 33623->33620; refs: 349191
Log: Game class is 'CinematicGame'
Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 3.349199...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Log: ALAudio: Using ALC_EXT_capture to record audio.
ScriptLog: New Player PoopyTheJ id=33550fa87c203526bd4c3ecc7693f6ef
Log: TTS: No output filename specified.
Log: Enter SetRes: 1280x1024 Fullscreen 1
Log: OpenGL
Log: GL_VENDOR     : ATI Technologies Inc.
Log: GL_RENDERER   : ATI Radeon HD 3850
Log: GL_VERSION    : 2.1.7412 Release
Log: OpenGL: Device supports: GL
Log: OpenGL: Device supports: GL_EXT_bgra
Log: OpenGL: Device supports: GL_ARB_texture_compression
Log: OpenGL: Device supports: GL_EXT_texture_compression_s3tc
Log: OpenGL: Device supports: GL_ARB_texture_cube_map
Log: OpenGL: Device supports: GL_ARB_texture_env_combine
Log: OpenGL: Device supports: GL_ATI_texture_env_combine3
Log: OpenGL: Device supports: GL_ARB_texture_env_crossbar
Log: OpenGL: Device supports: GL_EXT_texture_lod_bias
Log: OpenGL: Device supports: GL_ARB_multitexture
Log: OpenGL: Device supports: GL_ARB_multisample
Log: OpenGL: Device supports: GL_EXT_texture_filter_anisotropic
Log: OpenGL: Device supports: WGL_EXT_swap_control
Log: OpenGL: Missing function 'wglSwapIntervalEXT' for '_WGL_EXT_swap_control' support
Log: OpenGL: Device supports: GL_ARB_vertex_buffer_object
Log: OpenGL: Device supports: GL_ARB_fragment_program
Log: OpenGL: Device supports: GL_ARB_vertex_program
Log: OpenGL: Device supports: GL_EXT_framebuffer_object
Log: OpenGL: Device supports: GL_ARB_texture_non_power_of_two
Log: OpenGL: C32 RGB888 Z24 S8
Log: OpenGL: Level of anisotropy is 1.000000 (max 16.000000).
Log: OpenGL: Have 1 multisamples buffer, 2 samples.
Log: OpenGL: Using multisample (1 buffers, 2 samples)
Log: OpenGL: Forcibly disabled pixel shaders.
Log: OpenGL: Forcibly disabled render-to-texture.
Log: Startup time: 3.232350 seconds
Log: 
Developer Backtrace:
Log: [ 1]  /usr/local/games/ut2004/System/ut2004-bin-linux-amd64 [0xb29bad]
Log: [ 2]  /lib/libpthread.so.0 [0x2acd59159100]
Log: [ 3]  /usr/local/games/ut2004/System/ut2004-bin-linux-amd64(_Z13appDebugBreakv+0x25) [0xb239f5]
Log: [ 4]  /usr/local/games/ut2004/System/ut2004-bin-linux-amd64(_Z7appMsgfiPKwz+0xfd) [0xb2254d]
Log: [ 5]  /usr/local/games/ut2004/System/ut2004-bin-linux-amd64(main+0x3412) [0x52f212]
Log: [ 6]  /lib/libc.so.6(__libc_start_main+0xf4) [0x2acd59c49b44]
Log: [ 7]  /usr/local/games/ut2004/System/ut2004-bin-linux-amd64(strcat+0xaa) [0x52bc2a]
Log: Unreal Call Stack: appDebugBreak
Exit: Exiting.
Log: FileManager: Reading 0 GByte 40 MByte 457 KByte 111 Bytes from HD took 0.081608 seconds (0.081608 reading, 0.000000 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Allocation checking disabled
Uninitialized: Log file closed, Mon Apr 14 22:47:33 2008

---

### Post by Ideastone on 2008-04-15
I think your best bet is to apply all the latest patches, driver updates to ubuntu, and then try a clean install of UT. Otherwise, you'll probably just end up banging your head against the wall with your current config.

---

### Post by mjp216 on 2008-04-15
i have the latest patch and drivers, i reinstalled and to my avail.... no luck, i will not stop until this works, i dont really want it THAT bad but i am determined to get this fixed!!!
maybe ID should test their linux installers b4 shipping it out on cds.

---

### Post by dstone2004 on 2008-05-14
I have Ubuntu 8.04 (fully updated) and an ATI x1600 512mb AGP video card with the proprietary drivers.

glxgears shows the ATI running at about 2400FPS.

I downloaded and installed the UT2004 DEMO, it's a .run file.

It installs ok but when I try to run it nothing happens.

When I type ut2004 in the terminal window I get this error:

./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory



I tried a few things from other threads and forums, but nothing seems to work.


EDIT:

I uninstalled and re-installed the ut2004 demo (in the /home/lll/ut2004/ folder), and this time I noticed these errors in the terminal window, during installation:

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkEntry'

Gtk-CRITICAL **: file gtkentry.c: line 534 (gtk_entry_get_text): assertion `entry != NULL' failed.
Warning: kbuildsycoca is unable to register with DCOP.
kbuildsycoca running...
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/lll/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/lll/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/lll/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/lll/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file

---

