---
title: "enemy territory quake wars"
date: 2009-04-24
forum: Gaming &amp; Leisure
---

### Post by Cresho on 2009-04-24
Any reason why this game runs so slow in jaunty jackalope but runs fine in hardy heron?  It slows down during intense fights!  I never had this problem.

---

### Post by Vadi on 2009-04-24
What video card?

---

### Post by Cresho on 2009-04-24
BFG 8800gt OC

2gb ddr800

amd 6400 black edition

2 terabyte disk space







PC was running fine before.  Flash 10 on full screen also plays slow.  WIth compiz on or off, its the same.

---

### Post by Vadi on 2009-04-24
Got the latest drivers from hardware drivers thing?

Going to upgrade now myself, 8600gt here... will see how it goes.

---

### Post by Cresho on 2009-04-24
ya its updated, I actually downgraded.

Im going to try the beta drivers and if not, ill move back to hardy heron.

its like 3d acceleration and video acceleration is cut in half in speed.

---

### Post by Cresho on 2009-04-24
ya well i just updated to NVIDIA-Linux-x86_64-185.18.04-pkg0.run

My review of this combination with jaunty jackalope is bad...in my case.

THe drivers are new, x is new, adobe flash player needs to get fixed.

Enemy territory quake wars now gets a libGL.so.1 error.  I think ill head back to hardy heron 32 bit.  Jaunty jackalope is either too beta, needs patching, flash is slow, x is too new!  It still needs ironing out.  I think I'll wait till the next LTS.  LTS has not failed me yet.

at least I'm not going back to windows right?

funny thing the only reason I wanted to try jaunty was for KDEnlive and DIGIKAM.  I currently run vegas 8 in virtualbox and use picasa for those 2 applications.  It's not a complete waste of time since I tar my root and it only takes about 15 minutes to completely restore all my applications and previous system.

---

### Post by eragon100 on 2009-04-24
The driver version you guys mention is the beta version of Nvidia's new release series. The latest stable drivers work fine with Jaunty as well and, altough I haven't tried ET:QW with those drivers yet, the absolutely 100% awesome native linux free game [Savage: XR]("www.newerth.com") (In public beta, but runs perfectly. Awesome!) runs every bit as fast on Jaunty here as it does on intrepid ;)

I am going to try ET:QW now, see if that runs equally fast too. By the way, my video card is also a GeForce 8, namely a 512 MB DDR2 GeForce 8 8600 GT.

---

### Post by rizzeh on 2009-04-24
QW:ET read me suggests low latency kernel, anyone tried it?

---

### Post by eragon100 on 2009-04-24
Okay I tried, it's indeed (much) slower than with intrepid, even without a nice fight going on :(

---

### Post by Perfect Storm on 2009-04-24
and compiz is disable etc. ?

Haven't tried ETQW on ubuntu 9.04 going to give it a whirl now.

---

### Post by Cresho on 2009-04-24
wow!  I'm glad I'm not the only one and this means its not isolated to my system.  It is slow!  in a nice firefight, it bogs down to 3fps.  with or without compiz and I even dropped down the settings to minimum in all nvidia drivers and also in the game itself.  I even did a custom execution in an sh script to enable full ram support and multi thread.

One thing I give jaunty credit for is they got video sync with desktop refresh rate correct.  No choppiness or splitting.  I'm surprised nobody cought this.  Its either a etqw patch needed, nvidia drivers needing optimization, its just too crazy for me to deal with bugs since I have my hardy the way I like it.

jaunty is slow as a turtle with my current rig playing etqw.  is real time kernel working?  i tried it in the betas and it failed as well.

btw, i play as propellerhead.

---

### Post by Cresho on 2009-04-24
> **rizzeh said:**
> QW:ET read me suggests low latency kernel, anyone tried it?

[http://ubuntuforums.org/showthread.php?t=1084343](http://ubuntuforums.org/showthread.php?t=1084343)


ya i tried lots of things.  I'm not a newb you know. Well I am but I know what to do.  Flash player adobe version 10 works like the 9 did in hardy.  You can't go fullscreen!  flashplayer 10 works fine in hardy heron and not in jaunty.  A patch or update is needed.

So my 2 issues are

flashplayer in mozilla
3d games.

---

### Post by eragon100 on 2009-04-24
> **Cresho said:**
> [http://ubuntuforums.org/showthread.php?t=1084343](http://ubuntuforums.org/showthread.php?t=1084343)


ya i tried lots of things.  I'm not a newb you know. Well I am but I know what to do.  Flash player adobe version 10 works like the 9 did in hardy.  You can't go fullscreen!  flashplayer 10 works fine in hardy heron and not in jaunty.  A patch or update is needed.

So my 2 issues are

flashplayer in mozilla
3d games.

Flashplayer works fine for me, as do all games (including windows games under wine) except for ET:QW, which runs fine too, just a bit slower.

@A.I.: Yep, compiz is disabled.

---

### Post by Perfect Storm on 2009-04-24
Seems to work fine here even with compiz enable.
Running kubuntu 9.04
card: 8800 gtx 768mb
launching the etqw-rthread instead the normal as my comp support it.

I havn't checked FPS as I can't find the "~" key on my danish keyboard and the game is english (alt+ctrl+~).
com_showfps 1

---

### Post by rizzeh on 2009-04-24
add to autoexec.cfg

seta com_allowConsole 1
seta com_showfps 1

---

### Post by eragon100 on 2009-04-24
> **Artificial Intelligence said:**
> Seems to work fine here even with compiz enable.
Running kubuntu 9.04
card: 8800 gtx 768mb
launching the etqw-rthread instead the normal as my comp support it.

I havn't checked FPS as I can't find the "~" key on my danish keyboard and the game is english (alt+ctrl+~).
com_showfps 1

Thanx for posting the command! I didn't even know how to open the terminal :redface:

---

### Post by Perfect Storm on 2009-04-24
Doh, why didn't I look at the config file :popcorn:

okay. I'm getting 62 fps on 1680x1050 full graphic while compiz running in the background. When everything is blown up and alot of action appears moments I get average ~40 fps.

---

### Post by Cresho on 2009-04-24
maybee my resolution is the problem?  1920x1200 all settings maxed out.  I dropped all settings to minimum and still.  I don't have an issue with hardy heron

o btw, i can play 3d games fine but I meant to say intense 3d games like etqw is giving me problems during intense attacks and many players next to me.

What version flash are you using?

---

### Post by gotthardt on 2009-04-24
Very slow for me too. I just upgraded to 9.04 and ETQW is slow. Gets between 15 and 5 FPS. I tried different drivers from NVidia, but they do not help. I need to go back unless there is a fix. Is the the new X? or the new kernel? or?

sigh

---

### Post by Perfect Storm on 2009-04-25
Perhaps, those who have bad performance could compared their stuff, to find what they have in common. Because I don't have poor performance.

---

### Post by eragon100 on 2009-04-25
Great! :(

I installed kubuntu 9.04 to try it, then reinstalled a clean version of regular ubuntu 9.04 because KDE 4 was still horrid. Now on this new install, with the latest official nvidia driver, it won't work at all anymore. It starts, but after a few seconds in the menu (not even enough time to "log in"), it chrashes with a segmentation fault. Doesn't matter if compiz is enabled or not. Both the normal and the threaded renderer have this problem.

console output:

edward@alchemy-lab:~$ ./etqw
bash: ./etqw: No such file or directory
edward@alchemy-lab:~$ cd Desktop/games/etqw/
edward@alchemy-lab:~/Desktop/games/etqw$ ls
base            etqw-rthread      libgcc_s.so.1       readme_1_5_patch.txt
copyrights.txt  etqw-rthread.x86  libjpeg.so.62       README.txt
etqw            etqwtv.txt        libSDL-1.2.id.so.0  sdl.1.2.12.patch
etqw-dedicated  etqw.x86          libstdc++.so.6      server_readme.txt
etqwded.x86     EULA.txt          openurl.sh
etqw_icon.png   libCgx86.so       pb
edward@alchemy-lab:~/Desktop/games/etqw$ 
edward@alchemy-lab:~/Desktop/games/etqw$ ./etqw
ETQW 1.5.12663.12663  linux-x86 May  9 2008 13:50:52
found interface lo - loopback
found interface eth0 - 192.168.1.70/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/edward/Desktop/games/etqw/base/game000.pk4 with checksum 0x3efd73a5
Loaded pk4 /home/edward/Desktop/games/etqw/base/game001.pk4 with checksum 0xa02f1c18
Loaded pk4 /home/edward/Desktop/games/etqw/base/game002.pk4 with checksum 0x87457e61
Loaded pk4 /home/edward/Desktop/games/etqw/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /home/edward/Desktop/games/etqw/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /home/edward/Desktop/games/etqw/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /home/edward/Desktop/games/etqw/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /home/edward/Desktop/games/etqw/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /home/edward/Desktop/games/etqw/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /home/edward/Desktop/games/etqw/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /home/edward/Desktop/games/etqw/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /home/edward/Desktop/games/etqw/base/pak008.pk4 with checksum 0x71a93b80
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_english003.pk4 with checksum 0xc2d7ed49
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_french003.pk4 with checksum 0x8f315c7b
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_german003.pk4 with checksum 0x370e6186
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_korean003.pk4 with checksum 0x4f8dfac1
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_polish003.pk4 with checksum 0x8d9af876
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_russian003.pk4 with checksum 0x7e90b040
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Loaded pk4 /home/edward/Desktop/games/etqw/base/zpak_spanish003.pk4 with checksum 0xe7d989bc
Current search path:
/home/edward/.etqwcl/base
/home/edward/Desktop/games/etqw/base
/home/edward/Desktop/games/etqw/base/zpak_spanish003.pk4 (6 files)
/home/edward/Desktop/games/etqw/base/zpak_spanish002.pk4 (119 files)
/home/edward/Desktop/games/etqw/base/zpak_spanish001.pk4 (13 files)
/home/edward/Desktop/games/etqw/base/zpak_russian003.pk4 (5 files)
/home/edward/Desktop/games/etqw/base/zpak_russian002.pk4 (119 files)
/home/edward/Desktop/games/etqw/base/zpak_russian001.pk4 (13 files)
/home/edward/Desktop/games/etqw/base/zpak_polish003.pk4 (6 files)
/home/edward/Desktop/games/etqw/base/zpak_polish002.pk4 (119 files)
/home/edward/Desktop/games/etqw/base/zpak_polish001.pk4 (13 files)
/home/edward/Desktop/games/etqw/base/zpak_korean003.pk4 (5 files)
/home/edward/Desktop/games/etqw/base/zpak_korean002.pk4 (12 files)
/home/edward/Desktop/games/etqw/base/zpak_korean001.pk4 (12 files)
/home/edward/Desktop/games/etqw/base/zpak_korean000.pk4 (6 files)
/home/edward/Desktop/games/etqw/base/zpak_german003.pk4 (5 files)
/home/edward/Desktop/games/etqw/base/zpak_german002.pk4 (119 files)
/home/edward/Desktop/games/etqw/base/zpak_german001.pk4 (13 files)
/home/edward/Desktop/games/etqw/base/zpak_french003.pk4 (14 files)
/home/edward/Desktop/games/etqw/base/zpak_french002.pk4 (119 files)
/home/edward/Desktop/games/etqw/base/zpak_french001.pk4 (13 files)
/home/edward/Desktop/games/etqw/base/zpak_english003.pk4 (7 files)
/home/edward/Desktop/games/etqw/base/zpak_english002.pk4 (117 files)
/home/edward/Desktop/games/etqw/base/zpak_english001.pk4 (9 files)
/home/edward/Desktop/games/etqw/base/zpak_english000.pk4 (1018 files)
/home/edward/Desktop/games/etqw/base/pak008.pk4 (1496 files)
/home/edward/Desktop/games/etqw/base/pak007.pk4 (1510 files)
/home/edward/Desktop/games/etqw/base/pak006.pk4 (3 files)
/home/edward/Desktop/games/etqw/base/pak005.pk4 (2172 files)
/home/edward/Desktop/games/etqw/base/pak004.pk4 (72 files)
/home/edward/Desktop/games/etqw/base/pak003.pk4 (1133 files)
/home/edward/Desktop/games/etqw/base/pak002.pk4 (1637 files)
/home/edward/Desktop/games/etqw/base/pak001.pk4 (1067 files)
/home/edward/Desktop/games/etqw/base/pak000.pk4 (9350 files)
/home/edward/Desktop/games/etqw/base/game002.pk4 (3 files)
/home/edward/Desktop/games/etqw/base/game001.pk4 (11 files)
/home/edward/Desktop/games/etqw/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3566Kb
------------------------------
execing 'etqwconfig.cfg'
r_useThreadedRenderer is read only.
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
thread priority set to 1
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1680x1050
SDL_ListModes:
1680x1050 1440x900 1400x1050 1360x768 1360x765 1280x1024 1280x960 1152x864 1024x768 960x600 960x540 
840x525 832x624 800x600 720x450 700x525 680x384 640x480 512x384 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports -2144040 - broken?
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
X..GL_EXT_texture_rectangle not found
...using GL_EXT_stencil_wrap
...using GL_EXT_stencil_two_side
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_EXT_depth_bounds_test
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
...using GL_EXT_framebuffer_object
...using GL_EXT_packed_depth_stencil
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
...using GL_ARB_shader_objects
...using GL_ARB_vertex_shader
...using GL_ARB_fragment_shader
...using GL_ARB_fragment_program_shadow
...using GL_ARB_shadow
...using GL_ARB_depth_texture
...using GL_EXT_gpu_program_parameters
...using GL_EXT_timer_query
X..GL_GREMEDY_string_marker not found
...using GL_EXT_texture_compression_latc
---------- R_ARB2_Init ----------
Cg available.
---------------------------------
thread priority set to 2
thread priority set to 2
using ARB_vertex_buffer_object memory
renderSystem initialized.
--------------------------------------
72 strings read from localization/english/strings/bindings.lang
486 strings read from localization/english/strings/chat.lang
884 strings read from localization/english/strings/code.lang
2187 strings read from localization/english/strings/game.lang
3208 strings read from localization/english/strings/guis.lang
3384 strings read from localization/english/strings/lifestats.lang
3522 strings read from localization/english/strings/loadtips.lang
3861 strings read from localization/english/strings/locations.lang
4386 strings read from localization/english/strings/maps.lang
4453 strings read from localization/english/strings/tasks.lang
/proc/cpuinfo CPU frequency: 1600 MHz
Couldn't open journal files
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.18
opened Alsa PCM device default for playback
device buffer size: 5461 frames (21844 bytes)
allocated a mix buffer of 16384 bytes
--------------------------------------
-------- ALSA Microphone Init --------
device buffer size: 2910 frames (5820 bytes)
microphone initialized
--------------------------------------
initializating SDL Joysticks
initialized 0 controller(s)
-------- Initializing Session --------
----------------- BSE Init ------------------
--------- BSE Created Successfully ----------
session initialized
--------------------------------------
found DLL in pak file: /home/edward/Desktop/games/etqw/base/game002.pk4/gamex86.so
copy gamex86.so to /home/edward/.etqwcl/base/gamex86.so
game using generic code for SIMD processing
enabled Flush-To-Zero mode
--------- Initializing Game ----------
gamename: baseETQW-1
gamedate: May  8 2008
Initializing global UI namespaces
...23 namespaces
...240 properties
Initializing event system
...903 event definitions
Initializing class hierarchy
...163 classes, 397320 bytes for event callbacks
WARNING: Couldn't load sound 'video/intro_1024x512.theora', defaulting
WARNING: idDeclLocal::ParseLocal Failed to Parse decl 'video/intro' in file 'sounds/cinematics.sndshd' line 0
game initialized.
--------------------------------------
------------- Initialized in 13 -------------
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 12240
1600 MHz CPU
2976 MB System Memory
detecting video ram (set sys_videoRam on command line to override) ..
found XNVCtrl extension 1.17
512 MB Video Memory
Async thread started
Opening IP socket: localhost:-1
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
couldn't exec '/home/edward/.etqwcl/sdnet/eragon2890/base/autoexec.cfg'
execing /home/edward/.etqwcl/sdnet/eragon2890/base/profile.cfg 
execing 'localization/english/defaultbinds.cfg'
execing /home/edward/.etqwcl/sdnet/eragon2890/base/bindings.cfg 
snd_pcm_writei 4096 frames failed: Broken pipe
failed to recover from SND_PCM_STATE_XRUN: Input/output error
etqw.x86: pcm_pulse.c:361: pulse_write: Assertion `pcm->stream' failed.
double fault: 'Segmentation fault', bailing out
shutdown terminal support
0xe611bb80
[0x082e80e1]
[0x081a4a12]
[0x082e5ad0]
[0x082e1000]
[0x082e5521]
[0xf7fd4400]
[0x082e545c]
[0xf7fd4400]
[0xf7fd4430]
[0xf7b869a0]
[0xf7b88368]
[0xf7b7f62e]
[0xf6ec7e33]
[0xf7b1eaa1]
[0xf7ad9acc]
[0xf7b1eea5]
[0xf7ad43a4]
[0x08403f76]
[0x0840402b]
[0x084060b8]
[0x0844a71b]
[0x0844aaf6]
[0x08459a00]
[0x0819abaa]
[0x0819ac68]
[0x082e69b5]
[0xf7f0b4ff]
[0xf7c41b9e]
********************
ERROR: ERROR: pthread_join Async failed

********************
terminate called after throwing an instance of 'idException'
Aborted

To me, it looks suspiciously much like a problem with pulseaudio, but doesn anyone know of a way to fix it? :(

---

### Post by Cresho on 2009-04-25
I was on the 64 bit version and I got a libGSL.so.1 error and that is where I drew the line.  I went back to hardy.  I spent alot of time getting it the way I want and the "in between releases" have always been betas to me.  The LTS I stick to because in those releases, I can work with my system till i like it and make it perfect. and also long time support.

my system is not broken, just I don't want to upgrade and loose production time.  Ill wait till next beta release or the next lts.

besides, pulseaudio sounds horrible on my system and that would be a second issue i would have to deal with and also no mic recording for speach in ETQW.

They have to fix that as well.

---

### Post by Perfect Storm on 2009-04-25
Well, use the version of Ubuntu that works best for you. It's supported a long time yet. :)

---

### Post by Vadi on 2009-04-25
Getdeb will be supporting LTS + latest too. (so no intrepid now. sry intel video card folks)

---

### Post by eragon100 on 2009-04-25
I got the game working again. It was indeed pulseaudio. If you get the same chrash as me, just kill pulseaudio process. It will play fine and give sound trough alsa :wink:

---

### Post by eragon100 on 2009-04-25
And without soft particles, anistropy, and at 1440x1050 resolution, it's actually running fast, at least if there aren't any nice firefights going on. (But I think it will stay fast even when the fun starts :))

---

### Post by Cresho on 2009-04-25
> **eragon100 said:**
> I got the game working again. It was indeed pulseaudio. If you get the same chrash as me, just kill pulseaudio process. It will play fine and give sound trough alsa :wink:

ya thats a darn shame.  Pulseaudio is where ubuntu is heading.  Its not fixed and even the mixer is funky.  When I was playing with the mixer and forgeting about the game, The mixer doesnt keep the settings.  I had to do tons of work in hardy heron to make my mic work all the time.  It wasnt a problem at all but its perfect!.  After that, I would then need to get my 3 television tuners including an hdtv tuner in my pc to work and my video record in for vhs.  It is a whole package.  My linux does it all and if it's missing something, i throw a fit i guess.

My problem on the 64 bit was the file i mentioned and i already tossed the 32 bit disk thinking 64 was going to help.


Running the game with the system monitor revealed like 700mb used for game and around 50% cpu usage on both cores.  My GPU was not even hot and in the green area.  I need my game running at 1920x1200 with all affects.  and its a darn shame too because its fine in hardy.


One thing I want is the video sync.  It works for jaunty fine.  Hardy has some issues even after I tweaked it.

---

### Post by BanjoPants on 2009-04-26
Has anyone had the problem where you're playing for 10 or 15 minutes and then the game exits to a smaller window and the system essentially locks up?  I thought it was only a problem with Quake but after upgrading to Intrepid and playing Urban Terror the same thing happened.  I've searched the forums and haven't found anything but any ideas would be appreciated.

---

### Post by Perfect Storm on 2009-04-26
> **BanjoPants said:**
> Has anyone had the problem where you're playing for 10 or 15 minutes and then the game exits to a smaller window and the system essentially locks up?  I thought it was only a problem with Quake but after upgrading to Intrepid and playing Urban Terror the same thing happened.  I've searched the forums and haven't found anything but any ideas would be appreciated.

1) disable compiz
2) disable screensaver

---

### Post by Cresho on 2009-04-26
> **BanjoPants said:**
> Has anyone had the problem where you're playing for 10 or 15 minutes and then the game exits to a smaller window and the system essentially locks up?  I thought it was only a problem with Quake but after upgrading to Intrepid and playing Urban Terror the same thing happened.  I've searched the forums and haven't found anything but any ideas would be appreciated.

ya i had that problem as well.  It jumps out of the game in fullscreen or it completely shuts down.

ai figured it out but it still doesnt solve the constant crash i had.

---

### Post by Cresho on 2009-04-26
Well, I broke down and decided to install jaunty jackalope.

It went well this time.  Now my flash 10 and etqw works but I seem to miss something.  HOw did it work?

well:

I installed, updated, installed nvidia drivers, installed perfectbuntu and it works.It's strange.  The It could also be I also installed my drivers for my HDTV card.  I don't know but its working.

Thanks AI for the info on screensaver.  It seems to work and have not expirienced crashes.

Now to fix my Audio problem............DRAT!

---

### Post by Cresho on 2009-04-26
Here is something that just happened.  WHen I hit my mic to speak into, my game crashed and I was back on the desktop.  Any Ideas?

Jaunty jackalope.  Everything else seems to be working fine.

---

### Post by Cresho on 2009-04-28
Okay!  I got this thing working.  Its smooth and now my microphone is fixed.

first thing I did was disable the vsync and then did the soft particle disabling.  those 2 are the only thing I have disabled in the etqw game.  Everything else is bumped up to the max 1920x1200 resolution.

for my microphone fix is a bit more complicated.  I added a bipass on the pulse audio to the command.



WARNING!!!!!!!!!!!!!512 is the amount of memory on my video card.  replace this part with the amount of yours.
```

#!/bin/bash
killall compiz.real &
metacity --replace &

sleep 4 && amixer -q set "Mic Capture" 100% unmute;

pasuspender && sleep 1 && ./etqw-rthread +set com_allowConsole 1 +seta com_unlock_timingMethod "1" +seta com_unlockFPS "1"  +seta com_unlock_maxfps "90" +seta com_videoRam "512" +seta r_useThreadedRenderer "2";

compiz --replace &
metacity --replace &

```

My microphone problem in jaunty jackalope was also fixed by forcing my main audio device to be running ontop and using [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

ill post my device forcing here.

```
this is how I did it.

in the terminal

"asoundconf list"

then it spat out this

asoundconf list
Names of available sound cards:
Audigy2
SAA7134


So then I created a script

#!/bin/bash
sleep 10 && asoundconf set-default-card Audigy2;

and forced executable and forced it to autoboot in sessions under preferences.  Now my sound recorder works and I can record from mic no problem but audacity still sucks.  How can I Fix my problem?



additional info

also-oss
sox

these are also installed but not sure if this fixed the problem

sudo apt-get install asoundconf-gtk  or install this in synaptic.


asoundconf-gtk
```

in recording portion of alsa mixer, i only have analog mix capture up and mic capture up.  the rest is down including pcm.  There are other tweaks i added but I don't think it affects this.

---

### Post by Vadi on 2009-04-28
Thanks a bunch for this. Haven't installed etqw yet but would soon probably.

---

### Post by Cresho on 2009-04-28
ya just be careful.  I have no intent of cleaning up my notes but I have read tons of fixes and this one was the most easiest.  The first code was the first one which fixes lots of my issues. so go by that one first.  THe mic fix is not needed but it forces the card to be used first.  make sure you set your video ram correctly on the first code I posted.

---

### Post by klerfayt on 2009-05-02
#edit: originally I thought the performance degradation was pulseaudio related, but removing it with --purge only got rid of weird lags, the game still performs crappier (last Ubuntu release on which this game performed adequately remains still 7.10; maybe it's the combination of X.Org Server and the game itself?)

---

### Post by Cresho on 2009-05-06
i went back to hardy heron.  Jaunty was not running as good as I wanted it.

---

### Post by frodon on 2009-05-06
Anyone else playing QW on jaunty ?

Hope i won't have those MIC issues after upgrading, MIC is really useful for teamwork ingame.

Except this i play all at max and the only bug i have so far is that randomly after a map or 2 my framerate drop to 30 FPS and the game lag. Only way to solve this is to exit the game and restart it, highly annoying when you play on full server and then can't reconnect because of full server after exiting.

---

### Post by klerfayt on 2009-05-06
> **frodon said:**
> Anyone else playing QW on jaunty ?

Hope i won't have those MIC issues after upgrading, MIC is really useful for teamwork ingame.

Except this i play all at max and the only bug i have so far is that randomly after a map or 2 my framerate drop to 30 FPS and the game lag. Only way to solve this is to exit the game and restart it, highly annoying when you play on full server and then can't reconnect because of full server after exiting.
I would like to know also why this game performs much better in [Ubuntu 6.06]("http://releases.ubuntu.com/6.06/") if compared to more recent releases -- 8.04, 8.10 and 9.04

---

### Post by Perfect Storm on 2009-05-06
Because less stuff are running in the background and 6.06 do not have compiz enable. Use BUM to disable things you don't use and fusion-icon to disable compiz.

---

### Post by slambrick on 2009-05-06
> **Cresho said:**
> ya well i just updated to NVIDIA-Linux-x86_64-185.18.04-pkg0.run

My review of this combination with jaunty jackalope is bad...in my case.

THe drivers are new, x is new, adobe flash player needs to get fixed.

Enemy territory quake wars now gets a libGL.so.1 error.  I think ill head back to hardy heron 32 bit.  Jaunty jackalope is either too beta, needs patching, flash is slow, x is too new!  It still needs ironing out.  I think I'll wait till the next LTS.  LTS has not failed me yet.

at least I'm not going back to windows right?

funny thing the only reason I wanted to try jaunty was for KDEnlive and DIGIKAM.  I currently run vegas 8 in virtualbox and use picasa for those 2 applications.  It's not a complete waste of time since I tar my root and it only takes about 15 minutes to completely restore all my applications and previous system.

Did you know Picasa has a Linux client now?

---

### Post by klerfayt on 2009-05-06
> **Artificial Intelligence said:**
> Because less stuff are running in the background and 6.06 do not have compiz enable. Use BUM to disable things you don't use and fusion-icon to disable compiz.
No, I do not use compiz, neither have I any special services running (e.g. Tracker, Beagle or anything in system tray except volume control and network manager). I even went as far as trying "/" and "/home" with ext4 while doing clean install, benchmarking recorded demo with different CPU governors (where I discovered that suse sucks even more for gaming), trying nvidia beta drivers and disabling evdev for keyboard (setting AutoAddDevices to false in xorg.conf and specifying kbd, since my attempts to edit [fdi]("http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi") files ended with disaster). Oh well, I guess I have to go back to Windows, many applications perform ridiculously better there anyway (one of the more notorious examples being Firefox).

---

### Post by Perfect Storm on 2009-05-06
> **klerfayt said:**
> No, I do not use compiz, neither have I any special services running (e.g. Tracker, Beagle or anything in system tray except volume control and network manager). I even went as far as trying "/" and "/home" with ext4 while doing clean install, benchmarking recorded demo with different CPU governors (where I discovered that suse sucks even more for gaming), trying nvidia beta drivers and disabling evdev for keyboard (setting AutoAddDevices to false in xorg.conf and specifying kbd, since my attempts to edit [fdi]("http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi") files ended with disaster). Oh well, I guess I have to go back to Windows, many applications perform ridiculously better there anyway (one of the more notorious examples being Firefox).

Bye.

---

### Post by eragon100 on 2009-05-06
> **slambrick said:**
> Did you know Picasa has a Linux client now?

It doesn't. Google's "linux version" is the windows version bundled with a custom wine installation. Just look at the cursor inside the picasa window :wink:

---

### Post by Machinista on 2009-05-16
Guys, 

Re performance issues with Jaunty (and Intrepid).

I've found the following make a big difference:

1.  disabling dynamic tick and setting config-HZ = 1000 (customise kernel)
2.  launching game with 'etqw-rthread' to enable use of r_useThreadedRenderer = 2
3.  changing desktop effects to 'none'

The game gets FPS as high as my XP install, if not higher; prior to this it was a dog.

Still haven't got my mic to work and I get regular lag spikes every few minutes which I'm still trying to fix.

---

### Post by Redsunz on 2009-05-27
I'm running ETQW in Ubuntu 9.04 64 bit with Nvidia card and it runs great.  Except my play on line option is grayed out?  Any one else have that problem?

---

### Post by Bios Element on 2009-05-28
> **Redsunz said:**
> I'm running ETQW in Ubuntu 9.04 64 bit with Nvidia card and it runs great.  Except my play on line option is grayed out?  Any one else have that problem?

I can think of two solutions

#1: You need to make sure your net is working and a firewall isn't blocking it
#2: You need to make sure that you're not using any cracks as using them will disable online play.

---

### Post by Redsunz on 2009-05-29
> **Bios Element said:**
> I can think of two solutions

#1: You need to make sure your net is working and a firewall isn't blocking it
#2: You need to make sure that you're not using any cracks as using them will disable online play.

Thanks for the tips.
I tried disabling my firewall already and tried reinstalling ETQW still not working.  I think it must be something to do with Jaunty Jackalope as ETQW worked fine in Intrepid.

---

### Post by Bios Element on 2009-05-29
> **Redsunz said:**
> Thanks for the tips.
I tried disabling my firewall already and tried reinstalling ETQW still not working.  I think it must be something to do with Jaunty Jackalope as ETQW worked fine in Intrepid.

Might be, But I've been using ET:QW on Jaunty and it works 100% fine after I disable compiz and pulseaudio.

---

### Post by Redsunz on 2009-06-02
> **Bios Element said:**
> Might be, But I've been using ET:QW on Jaunty and it works 100% fine after I disable compiz and pulseaudio.

Yeah I disabled Compiz as well I could care less about flashy desktops.  I want my operating system to run quietly and reliably in the background with out any distractions.  :D Thats one of the main reasons I switched to Linux.
Are you running ETQW 1.5?
I have not had any problem with pulseaudio.  Maybe its my network card? "Grasping at straws here I really have no idea."

---

### Post by Barky on 2009-06-03
I'm having trouble with the microphone input for ET:QW. 

I can't select a capture device inside the drop down box of the voice tab in ET:QW. Everything else works fine, but I would like to get voice chat up and running. Any suggestions?

---

### Post by frodon on 2009-06-03
If you have only one sound card then it should be fine by default, if it isn't post back your etqw config file.
Remember that in etqw you need to push a button to talk.

---

### Post by Cresho on 2009-08-11
Hi all, After looking at kdenlive, I decided to update to jaunty.  Kdenlive now works fine when i split the video and audio by right clicking on the timeline and splitting.  rendering avchd files come out synced only in this mannter.

My original post as about etqw and sound and framerate problem and no mic.  I got that squared away.

I updated to 64bit, running 8800gt or gtx in anycase, and used the following lines to fix my issues.  Warning, this will uninstall pulseaudio.  This was one of the main reasons it caused my pc to fart alot.

also, this is an extremely short tutorial.

```
********************************************************************************
********************************************************************************
********************************************************************************
jaunty removing pulseaudio******************************************************
********************************************************************************
#killall pulseaudio
#sudo apt-get remove pulseaudio
#sudo apt-get install esound
#sudo rm /etc/X11/Xsession.d/70pulseaudio (do not do this just incase)
#Reboot system
********************************************************************************
********************************************************************************
********************************************************************************
test audio in also terminal*****************************************************
********************************************************************************
#speaker-test -Dplug:surround51 -c6 -twav
#speaker-test -Dplug:surround51 -c6 -l1 -twav
#speaker-test -Dplug:surround40 -c4 -l1 -twav
#speaker-test -Dplug:surround51 -c6 -l1 -twav
#speaker-test -Dplug:surround71 -c8 -l1 -twav
********************************************************************************
********************************************************************************
********************************************************************************
pulseaudio 5.1******************************************************************
********************************************************************************
#sudo gedit /etc/pulse/daemon.conf

Uncomment the line containing:
default-sample-channels = 2

and replace '2' with '6' (if you have a 7.1 card, replace '2' with '8')
Restart the window manager and enjoy the new sound!
********************************************************************************
********************************************************************************
********************************************************************************
mic fix*************************************************************************
********************************************************************************
#sudo apt-get install asoundconf-gtk
So then I created a script

##!/bin/bash
#sleep 10 && asoundconf set-default-card Audigy2;

and forced executable and forced it to autoboot in sessions under preferences.  Now my sound recorder works

other commands
#asoundconf set-default-card Audigy2
#asoundconf list
#
```


and a script that i use to fix the mic issue.  It basically opens up my mic automatically.  works most of the time.

```

#!/bin/bash

killall compiz.real &
metacity --replace &

sleep 4 && amixer -q set "Mic Capture" 95% unmute;


#run game;
cd ~/Installed_Programs/etqw
sleep 1 && ./etqw

compiz --replace &
metacity --replace &

```

this fixed the distorted sound caused by pulseaudio and no mic crash caused by pulseaudio.  Basically when i would hit send voice in game, it would kick me to the desktop.  This is the exact setup i had on my hardy and now it runs here.  What I always liked about jaunty is the vsync works!  compiz confige manager runs at a smooth 200fps and video is now synced to x.  compiz and x talk to each other now. :guitar:
finaly I can breath!

---

### Post by Morbett on 2009-08-11
Works perfectly!

---

