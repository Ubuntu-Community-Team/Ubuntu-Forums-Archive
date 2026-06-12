---
title: "Enemy Terriory / Dapper / i810 dark screen"
date: 2006-06-19
forum: Gaming &amp; Leisure
---

### Post by zordon on 2006-06-19
Already had some hard time with dapper with installing ipw2200/wpa_supplicant wi-fi for my laptop and finally found solution, but w/o wpa...hmmm... running quite happily in breezy, this dapper gives me another problem to solve.

As a fan of Wolfenstein: Enemy Territory I wanted to install it on fresh install of dapper with command:
```
sudo ./et-linux-2.55.x86-run.run
```
then rewriting files et.x86 and etded.x86 from 2.60b patch. Upto this point everything went smoothly. **BUT** (there is always some but). Typed et into command-line screen went blank/black with standard game sound :( . However, I could quit from blind (black) screen pressing ~ key for console and typing /quit, so it is some videographics **problem** for sure. 

No errors related to gfx while starting up et in console. It runs with sound but screen is blank and no errors at startup. Strange. Glxinfo reveals:
```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20050225
OpenGL version string: 1.3 Mesa 6.4.1
```
and ```
glxinfo | grep direct
direct rendering: Yes
```
while et refers (at startup/only interesting parts):
```

----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225
GL_VERSION: 1.3 Mesa 6.4.1
...
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(16-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled

```

full logs included in attachment (inc. xorg.conf) if somebody wants to dig deep

I tried several configurations and I also searched forums/web and didn't find a solutions. It seems to me, like opengl-output is just somehow disabled or what, because screen flashes and mouse cursor/pointer blinks and changes size at startup, so it's switching to right resolution. Or maybe it's that mesa thing. I also read something about i810 driver doesn't support 3d in xorg.7.0 very well, which would be sad news for me and dapper. 

I hope somebody can point me to right source of information I seek & were not able to find. Maybe somebody got the same problem / or knows more then me. 

What more diagnostics I can do?

---

### Post by gerbman on 2006-06-20
It doesn't look like you have 3D acceleration enabled. Has ET ever worked on your system? What kind of video card do you have? From your xorg file it looks like you have one of those integrated video deals...I'm not sure if ET will work without a dedicated video card.

---

### Post by handy on 2006-06-20
The i810, came along after the magnificent BX intel chipset.  It was a huge step backwards, unfortunately.

Integrated graphics, with very limited capabilities.

I am surprised that the i810 could run ET!  I expect that the chipset is at its very limit when doing so...

I'm sorry I can't help with a solution, I am only good for a little useless background info'.

---

### Post by zordon on 2006-06-20
It's centrino notebook w/ 1.7GHz P4 and i810 is driver; yes, it has integrated graphics. from lspci (log attached) I see it as 

Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

I had not problem with it in breezy and warthy. It just functioned. When set to 1024x768 16bit colors low-quality, Enemy Territory was quite playable.

Still no clue? Notebook isn't my primary gaming machine, but it would be nice to have it functioning.

---

### Post by handy on 2006-06-20
I am unfamiliar with your chipset.  I am glad that it is not really an i810! :) 

I still can be no help to you though, I am sorry.

---

### Post by Brucevdk on 2006-06-30
This is the latest thread concerning the "sound yes/screen no" problem I could find on these forums, if it's not please point me in the right direction. There are actually more threads discussing this problem, see below for the links.

I had the same problem and stumbled on this thread while looking for more information. I'm still looking into this issue at the moment, I have found a workaround but not yet the ideal solution. First let us compare hardware/settings, we do have the same chipset.

glxinfo reveals the following information:
```

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20050225
OpenGL version string: 1.3 Mesa 6.4.1

direct rendering: Yes

```

[SIZE="4"]The workaround[/SIZE]
Now the actual problem lies in the xorg.conf file and has to do with the HorizSync and the VertRefresh variables. If you want to get Enemy Territory to work you'll either have to uncomment or remove both from your config. After which the Monitor section should look like the following:

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	#HorizSync	28-64
	#VertRefresh	43-60
EndSection

```

You might also have to fool around with your in-game resolution settings, I could only use 800x600 and 640x480. As I said before this is only a workaround, the game will start and you will be able to play however the screen is not actually resized to the chosen resolution. The problem is best described over at the [ Freedesktop.org mailing lists]("http://lists.freedesktop.org/archives/xorg/2006-January/012399.html") (it may not be related). You will also not be able to switch resolutions in your window manager after removing the variables.

I advise you to reconfigure the xserver-xorg package, to avoid problems during the reconfiguration you should stop GDM first e.g.

```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg

```

You can find my current xorg.conf in the attachment section. I'm going to look into this some more, it just occured to me that there must obviously be some default settings to the vertical refresh rates so I'll take a look at that next.

P.S.
I haven't tested this anywhere else, so tell me if it doesn't work.

[SIZE="4"]Possibly related problems[/SIZE]
The problem seems to date back to at least October 2005, also looks like every user facing this exact problem has an Intel integrated video chipset.
[LIST]
[*] WishMaster, [*"Enemy Territory: sound, but no screen"*]("http://ubuntuforums.org/showthread.php?t=80926"), Ubuntu Forums (the thread was eventually hijacked by someone with an ATI video card and an actually unrelated problem)
[*] shreevatsa, [*"I can hear sound playing, but I can't see anything except the black screen."*]("http://www.ubuntuforums.org/showpost.php?p=504471&postcount=100"), Ubuntu Forums
[*] Wayne Smith, [*"855GM not changing resolutions for games"*]("http://lists.freedesktop.org/archives/xorg/2006-January/012399.html"), Freedesktop.org Mailing Lists
[/LIST]

[SIZE="4"]External links[/SIZE]
Here's a couple of useful links that might be of some assistance.
[LIST]
[*] [Enemy Territory Console Commands & Cvars]("http://www.rtcw.jolt.co.uk/content/enemy_territory/cmdcvarlist/index.html")
[*] [Screenshot of the available r_modes]("http://www.rtcw.jolt.co.uk/content/enemy_territory/cmdcvarlist/modelist.jpg")
[/LIST]

---

### Post by zordon on 2006-06-30
Yeah, that's it!

I just commented those lines from xorg.conf; restarted gdm and then edited .etwolf/etmail/etconfig.cfg (i think) r_mode "-1" r_customwidth 1024 and height 768 and colordepth to 16; but it started in 800x600 anyway aligned to o bottom left (as noted on some links you provided above); but it runs, which is step forward; - it shows something - game ;-) !

I hope I will se this bug fixed some time, because switching resolution from withing et doesn't work.

Anyway thank you for this partial solution. As my notebook isn't my primary gaming station, it's not so important to me, but at least I know (I guess), where is the problem.

---

