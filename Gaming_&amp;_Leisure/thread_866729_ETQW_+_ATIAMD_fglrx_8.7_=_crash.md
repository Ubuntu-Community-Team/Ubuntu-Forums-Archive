---
title: "ETQW + ATI/AMD fglrx 8.7 = crash"
date: 2008-07-22
forum: Gaming &amp; Leisure
---

### Post by soxs on 2008-07-22
I just installed fglrx 8.7 successfully, and tried to run ETQW.
It loaded all files fine.
Then the first sign of something ugly: The cursor was extremly slow.
I didn't think about and tried to run a singleplayer map. But as soon as I press the "go"/"start" button, I resume to the desktop, game is gone and the mouse refuses to move (I guess it's still captured by openGL)
I have to restart the X-server in order to make my PC useable again.

Thx for any answers/help.

EDIT: Nexuiz still works as supposed. I conclude its a SDL specific problem.

EDIT: Sauerbraten lags like hell, especially mouse movement.
EDIT: UrbanTerror4.1 and Warsow lag aswell.

Note: I own a phenom/RadeonHD3870 based system and had no problems running all the named games with "insane" settings using previous drivers.

---

### Post by soxs on 2008-07-22
log:
```
ETQW 1.5.12663.12663  linux-x86 May  9 2008 13:57:26
found interface lo - loopback
found interface eth0 - X.Y.0.Z/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /media/zer0/ETQW/base/game000.pk4 with checksum 0x3efd73a5
Loaded pk4 /media/zer0/ETQW/base/game001.pk4 with checksum 0xa02f1c18
Loaded pk4 /media/zer0/ETQW/base/game002.pk4 with checksum 0x87457e61
Loaded pk4 /media/zer0/ETQW/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /media/zer0/ETQW/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /media/zer0/ETQW/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /media/zer0/ETQW/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /media/zer0/ETQW/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /media/zer0/ETQW/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /media/zer0/ETQW/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /media/zer0/ETQW/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /media/zer0/ETQW/base/pak008.pk4 with checksum 0x71a93b80
Loaded pk4 /media/zer0/ETQW/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /media/zer0/ETQW/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /media/zer0/ETQW/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /media/zer0/ETQW/base/zpak_english003.pk4 with checksum 0xc2d7ed49
Loaded pk4 /media/zer0/ETQW/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /media/zer0/ETQW/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /media/zer0/ETQW/base/zpak_french003.pk4 with checksum 0x8f315c7b
Loaded pk4 /media/zer0/ETQW/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /media/zer0/ETQW/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /media/zer0/ETQW/base/zpak_german003.pk4 with checksum 0x370e6186
Loaded pk4 /media/zer0/ETQW/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /media/zer0/ETQW/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /media/zer0/ETQW/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /media/zer0/ETQW/base/zpak_korean003.pk4 with checksum 0x4f8dfac1
Loaded pk4 /media/zer0/ETQW/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /media/zer0/ETQW/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /media/zer0/ETQW/base/zpak_polish003.pk4 with checksum 0x8d9af876
Loaded pk4 /media/zer0/ETQW/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /media/zer0/ETQW/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /media/zer0/ETQW/base/zpak_russian003.pk4 with checksum 0x7e90b040
Loaded pk4 /media/zer0/ETQW/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /media/zer0/ETQW/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Loaded pk4 /media/zer0/ETQW/base/zpak_spanish003.pk4 with checksum 0xe7d989bc
Current search path:
$HOME/.etqwcl/base
/media/zer0/ETQW/base
/media/zer0/ETQW/base/zpak_spanish003.pk4 (6 files)
/media/zer0/ETQW/base/zpak_spanish002.pk4 (119 files)
/media/zer0/ETQW/base/zpak_spanish001.pk4 (13 files)
/media/zer0/ETQW/base/zpak_russian003.pk4 (5 files)
/media/zer0/ETQW/base/zpak_russian002.pk4 (119 files)
/media/zer0/ETQW/base/zpak_russian001.pk4 (13 files)
/media/zer0/ETQW/base/zpak_polish003.pk4 (6 files)
/media/zer0/ETQW/base/zpak_polish002.pk4 (119 files)
/media/zer0/ETQW/base/zpak_polish001.pk4 (13 files)
/media/zer0/ETQW/base/zpak_korean003.pk4 (5 files)
/media/zer0/ETQW/base/zpak_korean002.pk4 (12 files)
/media/zer0/ETQW/base/zpak_korean001.pk4 (12 files)
/media/zer0/ETQW/base/zpak_korean000.pk4 (6 files)
/media/zer0/ETQW/base/zpak_german003.pk4 (5 files)
/media/zer0/ETQW/base/zpak_german002.pk4 (119 files)
/media/zer0/ETQW/base/zpak_german001.pk4 (13 files)
/media/zer0/ETQW/base/zpak_french003.pk4 (14 files)
/media/zer0/ETQW/base/zpak_french002.pk4 (119 files)
/media/zer0/ETQW/base/zpak_french001.pk4 (13 files)
/media/zer0/ETQW/base/zpak_english003.pk4 (7 files)
/media/zer0/ETQW/base/zpak_english002.pk4 (117 files)
/media/zer0/ETQW/base/zpak_english001.pk4 (9 files)
/media/zer0/ETQW/base/zpak_english000.pk4 (1018 files)
/media/zer0/ETQW/base/pak008.pk4 (1496 files)
/media/zer0/ETQW/base/pak007.pk4 (1510 files)
/media/zer0/ETQW/base/pak006.pk4 (3 files)
/media/zer0/ETQW/base/pak005.pk4 (2172 files)
/media/zer0/ETQW/base/pak004.pk4 (72 files)
/media/zer0/ETQW/base/pak003.pk4 (1133 files)
/media/zer0/ETQW/base/pak002.pk4 (1637 files)
/media/zer0/ETQW/base/pak001.pk4 (1067 files)
/media/zer0/ETQW/base/pak000.pk4 (9350 files)
/media/zer0/ETQW/base/game002.pk4 (3 files)
/media/zer0/ETQW/base/game001.pk4 (11 files)
/media/zer0/ETQW/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Found $HOME/.etqwcl//etqw.pid - pid 9166
Removing stale lock file (/home/bernhard/.etqwcl//etqw.pid)
----- Initializing Decls -----
Decompressing the global token cache...3566Kb
------------------------------
execing 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
thread priority set to 1
couldn't exec '$HOME/.etqwcl/sdnet/soxs060389/base/autoexec.cfg'
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1280x1024
SDL_ListModes:
1280x1024 1280x960 1280x768 1280x720 1152x864 1024x768 800x600 720x576 720x480 640x480 640x432 
640x400 512x384 400x300 320x240 320x200 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
[B]no multisampling
vsync: SDL reports -4735176 - broken?[/B]
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
X..GL_EXT_texture_filter_anisotropic not found
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
...using GL_EXT_texture_rectangle
...using GL_EXT_stencil_wrap
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ARB_vertex_buffer_object not found
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..GL_EXT_depth_bounds_test not found
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
...using GL_EXT_framebuffer_object
X..GL_EXT_packed_depth_stencil not found
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
X..GL_ARB_shader_objects not found
X..GL_ARB_vertex_shader not found
X..GL_ARB_fragment_shader not found
X..GL_ARB_fragment_program_shadow not found
...using GL_ARB_shadow
...using GL_ARB_depth_texture
X..GL_EXT_gpu_program_parameters not found
X..GL_EXT_timer_query not found
X..GL_GREMEDY_string_marker not found
X..GL_EXT_texture_compression_latc not found
---------- R_ARB2_Init ----------
Cg available.
---------------------------------
[B]thread priority set to 2
thread priority set to 2
WARNING: vertex array range in virtual memory (SLOW)
renderSystem initialized.[/B]
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
/proc/cpuinfo CPU frequency: 1100 MHz
**Couldn't open journal files**
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libALSA lib ../../../src/pcm/pcm_dmix.c:996:(snd_pcm_dmix_open) unable to open slave
asound.so.2)
asoundlib version: 1.0.16
snd_pcm_open SND_PCM_STREAM_PLAYBACK 'default' failed: Device or resource busy
dlclose
**WARNING: sound subsystem disabled** #ignore this, is caused by running exaile(pullseaudio) in parallel

--------------------------------------
----------- Alsa Shutdown ------------
--------------------------------------
initializating SDL Joysticks
initialized 0 controller(s)
-------- Initializing Session --------
----------------- BSE Init ------------------
--------- BSE Created Successfully ----------
session initialized
--------------------------------------
found DLL in pak file: /media/zer0/ETQW/base/game002.pk4/gamex86.so
copy gamex86.so to /home/bernhard/.etqwcl/base/gamex86.so
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
------------- Initialized in 28 -------------
--- Common Initialization Complete ---
terminal support disabled: stdin is not a tty
pid: 7935
1100 MHz CPU
3968 MB System Memory
sys_videoRam is set to 512, override and skip detection
512 MB Video Memory
Async thread started
execing $HOME/.etqwcl/sdnet/$USER/base/profile.cfg 
execing 'localization/english/defaultbinds.cfg'
execing /home/bernhard/.etqwcl/sdnet/$USER/base/bindings.cfg 
PunkBuster Client: Attempting to resolve master7.evenbalance.com
PunkBuster Client: Resolved to [A.B.C.D]
PunkBuster Client: PunkBuster Client (v2.053 | A0) Enabled
Opening IP socket: localhost:-1
PunkBuster Client: Game Version [ETQW 1.5.12663.12663  linux-x86 May  9 2008 13:57:26]
PunkBuster Client: Not Connected to a Server
Opening IP socket/usr/bin/etqw: line 3:  7935 Segmentation fault      ./etqw-rthread
```

---

### Post by soxs on 2008-07-30
BUMP -.-
Did no one else get any problems with 8.7???
I will wait one more week before doing any attempt of reinstalling 8.6 and if that fails, ubuntu.

---

### Post by chewit on 2008-07-30
would using the opensource drivers be better? I have seen articles showing that you get better performance using the opensource dirvers than the official ATi ones.

Did you use envy to install the new driver?

---

### Post by soxs on 2008-07-30
> **chewit said:**
> would using the opensource drivers be better? I have seen articles showing that you get better performance using the opensource dirvers than the official ATi ones.

Did you use envy to install the new driver?

I am always doing it by hand, at least with the latest ones (8.6, 8.7)
And the opensource driver still lacks 3D acceleration. I will use the opensource one, when it got up to at least 70% of the proprietary fglrx.

---

### Post by chewit on 2008-07-31
It might be easy if you download Envy from the repos. It will download and install the correct drivers. It will even make sure you have the latest drivers as well.

Also, what do mean that the open source drivers lacks 3D support. I have Full 3D support on my ATi card.

---

### Post by soxs on 2008-07-31
> **chewit said:**
> It might be easy if you download Envy from the repos. It will download and install the correct drivers. It will even make sure you have the latest drivers as well.

Also, what do mean that the open source drivers lacks 3D support. I have Full 3D support on my ATi card.

which one do you own?
EDIT: see sig, 7000er, for that the opensource driver is the best choice of course, but I own a hellbesats: RadeonHD 3870 which requires the radonhd driver to work properly (at the opensource side) or the proprietary fglrx. The first one lacks (at least atm) 3D acceleration (not at all, but only watching glxgears doesn't make my day), so I am stuck with the fglrx driver. [I investigated a lot to make the proper choice for my driver and I am still waiting and watching out for either a "good" fglrx driver or a break through with the RadeonHD driver]

I need FULL 3D acceleration, accleration that uses the possibilities of my card and not just heating up for nothing (extremly spoken).

Note: I dislike envy, it worked the way I did the driver install for some releases now, and I am not going back to the blackboxmodel.

---

### Post by Vakman on 2008-08-01
> **chewit said:**
> Also, what do mean that the open source drivers lacks 3D support. I have Full 3D support on my ATi card.
Your ATI card works well!? I have not seen this in a while. If you could explain how? I have a Radeon Xpress 1200 and it works fine on Windows... which is why I am still dual-booted and not fully using Linux.

---

### Post by chewit on 2008-08-01
I used two tips which worked for me on the 'radeon' driver. If your using the 'ati' dirver, switch the 'radeon', better performance.
[URL="http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/"]
http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/[/URL]

[http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/]("http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/")

---

### Post by soxs on 2008-08-01
> **chewit said:**
> I used two tips which worked for me on the 'radeon' driver. If your using the 'ati' dirver, switch the 'radeon', better performance.
[URL="http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/"]
http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/[/URL]

[http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/]("http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/")

We are mainly talking about fglrx, not the opens source ones, at least my Xpress one works pretty fine with 8.6.

---

