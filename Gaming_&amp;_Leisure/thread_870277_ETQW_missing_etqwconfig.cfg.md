---
title: "ETQW: missing etqwconfig.cfg"
date: 2008-07-25
forum: Gaming &amp; Leisure
---

### Post by mufn8r on 2008-07-25
I finally got etqw installed, after 2 days of trying! Yay. While I was in the setting for the game I set the video to 1360x768 which worked OK. Now, when I try to run the game is states that that resolution is not in the list of possible choices. I decided to hunt down etqwconfig.cfg to manually choose the proper value but there is not such file on the entire partition. I'm guessing I have to actually go into the game, play and exit properly for the file to be created? If so, I'm stuck because I can't get into the game b/c of the error, I created myself. 

*shoots other foot*

I guess what I'm asking is, where is the etqwconfig.cfg file and what line do I put in it to fix this error?

---

### Post by mufn8r on 2008-07-25
Here's the output during etqw start up:

```
execing 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
execing 'autoexec.cfg'
Vendor: Device:
thread priority set to 1
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1280x1024
SDL_ListModes:
1280x1024 1280x960 1280x800 1280x768 1152x864 1152x768 1024x768 840x525 832x624 800x600 800x512 
720x450 720x400 640x512 640x480 640x400 640x384 640x350 576x432 576x384 512x384 
416x312 400x300 360x200 320x240 320x200 320x175 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: No video mode large enough for 1360x768
------- Initializing renderSystem --------
----- R_InitOpenGL -----
signal caught: 'Segmentation fault', si_code 1
callstack:
0x0
[0x082e80e1]
[0x082e549d]
[0xffffe600]
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()

```

---

### Post by mufn8r on 2008-07-25
Can't anyone help me with this? I really want to play ETQW.

---

### Post by boktor on 2008-08-07
The config file should be in /home/YOURUSERNAME/.etqwcl/base/etqwconfig.cfg

Look for
seta r_customHeight "768"
seta r_customWidth "1360"

Then put in the proper values.
Are you sure your monitor is set to at least 1360x768? Fixing that would also work.


Edit: Oh, and if that doesn't work then run the game like this
$ etqw +set r_fullscreen 0

---

