---
title: "quake 4 demo"
date: 2009-05-30
forum: Gaming &amp; Leisure
---

### Post by wolfyking2 on 2009-05-30
I start it, the screen goes black, exits, then the screen gets HUGE.  I can only see like, 1/8th of the screen.  It might have something to do with the shaders, because  I have an intel graphics card.

---

### Post by hikaricore on 2009-05-30
Yes just like every other game you've had trouble with it's your intel "graphics" hardware.
You will not be able to run Quake 4 on that hardware under Linux.

---

### Post by wolfyking2 on 2009-05-30
is there some way to disable the shaders without getting into the game

---

### Post by CharmyBee on 2009-05-30
no, shaders in Quake 4 are mandatory, essential, and can not run without them.

---

### Post by wolfyking2 on 2009-05-30
or shadows, or is there like an autoexec.cfg I can put in so I can set the game to lowest settings?

---

### Post by CharmyBee on 2009-05-30
If you can't even get to the menu, then you shouldn't even try playing the game. 
Try starting Quake4 in a terminal and see what errors it pops up with.

---

### Post by wolfyking2 on 2009-05-30
this is what I get

```
user@ubuntu:~$ '/home/user/quake4-demo/quake4.x86' 
Quake4 Demo Final V1.0.0 linux-x86 Nov 28 2005
found interface lo - loopback
found interface eth0 - 173.30.26.227/255.255.248.0
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/user/quake4-demo/q4base/game000.pk4 with checksum 0xc01bb9a0
Loaded pk4 /home/user/quake4-demo/q4base/game100.pk4 with checksum 0xe71d2aa2
Loaded pk4 /home/user/quake4-demo/q4base/pak001.pk4 with checksum 0x4a4195c2
Loaded pk4 /home/user/quake4-demo/q4base/zpak_english.pk4 with checksum 0xab62ab5e
Loaded pk4 /home/user/quake4-demo/q4base/zpak_french.pk4 with checksum 0x88c09a6b
Loaded pk4 /home/user/quake4-demo/q4base/zpak_italian.pk4 with checksum 0xb7cf593a
Loaded pk4 /home/user/quake4-demo/q4base/zpak_spanish.pk4 with checksum 0x1dec3532
Current search path:
/home/user/.quake4-demo/q4base
/home/user/quake4-demo/q4base
/home/user/quake4-demo/q4base/zpak_spanish.pk4 (864 files)
/home/user/quake4-demo/q4base/zpak_italian.pk4 (822 files)
/home/user/quake4-demo/q4base/zpak_french.pk4 (784 files)
/home/user/quake4-demo/q4base/zpak_english.pk4 (779 files)
/home/user/quake4-demo/q4base/pak001.pk4 (7663 files)
/home/user/quake4-demo/q4base/game100.pk4 (2 files)
/home/user/quake4-demo/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------

Running in restricted demo mode.

------------ Initializing Decls -------------
Loading guides.... 59 loaded
335ms to load 1064k of material
80ms to load 43k of skin
234ms to load 719k of sound
3ms to load 1k of materialType
387ms to load 2078k of lipSync
90ms to load 105k of playback
1092ms to load 1666k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
641 strings read from strings/english_code.lang
1669 strings read from strings/english_guis.lang
5631 strings read from strings/english_lips.lang
6100 strings read from strings/english_maps.lang
641 strings read from strings/french_code.lang
1668 strings read from strings/french_guis.lang
5630 strings read from strings/french_lips.lang
6099 strings read from strings/french_maps.lang
641 strings read from strings/italian_code.lang
1668 strings read from strings/italian_guis.lang
5630 strings read from strings/italian_lips.lang
6099 strings read from strings/italian_maps.lang
641 strings read from strings/spanish_code.lang
1668 strings read from strings/spanish_guis.lang
5630 strings read from strings/spanish_lips.lang
6099 strings read from strings/spanish_maps.lang
Couldn't open journal files
execing default.cfg
"ALT" isn't a valid key
"CTRL" isn't a valid key
couldn't exec editor.cfg
execing Quake4Config.cfg
execing autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother.
/dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_NV_blend_square
...using GL_ARB_texture_compression
X..GL_EXT_texture_compression_s3tc not found
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
user@ubuntu:~$ 


```

---

### Post by Wiebelhaus on 2009-05-30
> **hikaricore said:**
> Yes just like every other game you've had trouble with it's your intel "graphics" hardware.
You will not be able to run Quake 4 on that hardware under Linux.

I'd like to reiterate and clarify what hikaricore is saying , you will not be able to run graphic intensive games of any kind at all on any operating system , your system is not powerful enough for it. If your strapped for cash get an _***old reliable work horse***_ like [GF6800]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130461") Stable as a rock and supported by every OS know to man and dirt cheap.

---

### Post by wolfyking2 on 2009-05-31
It's not that were short on money.  My parents don't like to buy 'unnecessary' things, but we already have a lot of 'unnecessary' things.

---

### Post by simeon87 on 2009-05-31
> **wolfyking2 said:**
> It's not that were short on money.  My parents don't like to buy 'unnecessary' things, but we already have a lot of 'unnecessary' things.

But you could argue that this is 'necessary' :P

---

