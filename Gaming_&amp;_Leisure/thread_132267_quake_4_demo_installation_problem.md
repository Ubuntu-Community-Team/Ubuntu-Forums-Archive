---
title: "quake 4 demo installation problem"
date: 2006-02-18
forum: Gaming &amp; Leisure
---

### Post by krait on 2006-02-18
hi,

i downloaded and installed the quake 4 demo for linux. i then restarted and tried to run it, when i got this:

bash: quake4-demo: command not found
bharath@sparta:~/quake4-demo$ sh quake4-demo
Quake4 Demo Final V1.0.0 linux-x86 Nov 28 2005
found interface lo - loopback
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/bharath/quake4-demo/q4base/game000.pk4 with checksum 0xc01bb9a0
Loaded pk4 /home/bharath/quake4-demo/q4base/game100.pk4 with checksum 0xe71d2aa2
Loaded pk4 /home/bharath/quake4-demo/q4base/pak001.pk4 with checksum 0x4a4195c2
Loaded pk4 /home/bharath/quake4-demo/q4base/zpak_english.pk4 with checksum 0xab6 2ab5e
Loaded pk4 /home/bharath/quake4-demo/q4base/zpak_french.pk4 with checksum 0x88c0 9a6b
Loaded pk4 /home/bharath/quake4-demo/q4base/zpak_italian.pk4 with checksum 0xb7c f593a
Loaded pk4 /home/bharath/quake4-demo/q4base/zpak_spanish.pk4 with checksum 0x1de c3532
Current search path:
/home/bharath/.quake4-demo/q4base
/home/bharath/quake4-demo/q4base
/home/bharath/quake4-demo/q4base/zpak_spanish.pk4 (864 files)
/home/bharath/quake4-demo/q4base/zpak_italian.pk4 (822 files)
/home/bharath/quake4-demo/q4base/zpak_french.pk4 (784 files)
/home/bharath/quake4-demo/q4base/zpak_english.pk4 (779 files)
/home/bharath/quake4-demo/q4base/pak001.pk4 (7663 files)
/home/bharath/quake4-demo/q4base/game100.pk4 (2 files)
/home/bharath/quake4-demo/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------

Running in restricted demo mode.

------------ Initializing Decls -------------
Loading guides.... 59 loaded
970ms to load 1064k of material
105ms to load 43k of skin
200ms to load 719k of sound
17ms to load 1k of materialType
404ms to load 2078k of lipSync
73ms to load 105k of playback
1006ms to load 1666k of effect
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
couldn't exec Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
dlopen(libasound.so.2)
asoundlib version: 1.0.9
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 15052 frames ( 60208 bytes )
allocated a mix buffer of 16384 bytes
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

-------------------------------------------------------------------

So i was wondering if anyone ran into this problem. I have both SDL and glibc installed as was told on the download site. 

Some one do help, i have completely moved to ubuntu breezy and am findin it boring without any games.

thanks in advance.

cheers

---

### Post by krait on 2006-02-20
Is there no soul out there who can help me with this? i have noticed so many people mention that they got q4 running on this forum..

someone help.

cheers n thanks

---

### Post by aljones15 on 2006-02-20
it's come up before. I just re-installed quake 4 for the first time in awhile and got the same error. you're missing some open gl ARB files. not sure on how to get them.
search around answer might be here.

-
A

---

### Post by krait on 2006-02-20
i have spent nearly 2 hours trying to find something related to this. This is getting me really irritated. why cant ubuntu even properly run a linux application?
already we have only a few choices on our hands and now this....

some ubuntu genius out there, kindly help!!!!

cheers

---

### Post by Brynster on 2006-02-20
Hey Krait.

Just a quick question what video card are you running?

---

### Post by krait on 2006-02-20
hi,

i hav an IBM R51 with the following grafix card

Intel Corporation 82852/855GM Integrated Graphics Device

is that what you are referring to?

thanks n cheers

---

### Post by hav0x on 2006-02-20
LOL ...
Good luck running Q4 on that baby.
Btw: before going all "why cant ubuntu even properly run a linux application?", you should search the web for an answer to what you are doing wrong.
You need some sort of drivers for that videocard to be able to run glx applications.

---

### Post by krait on 2006-02-20
oh wonderful.

i need to go hunting for some video drivers to get this running!!

i checked my xorg.conf and it says i m using the i810 driver fr my i855GM. i checked on the net and found others wit the same using the i810 driver only.

I have never had problems running games on windows. i shud blame myself fr having deleted it, must have kept it fr games.

so wats the final word on this problem? if its not gonna work, i mite as well just move on, have spent more than the necessary amount of time. its a demo for christ's sake!!!

---

### Post by Jason_25 on 2006-02-20
I'm sorry but quake 4 isn't going to run on that sadly.

---

### Post by akiro.yamamoto on 2006-02-21
krait: If you check the requirements you will see that you NEED a 3D Accelerated Card to run Quake 4. There is no way to get around it, even if you use Windows you will still need a 3D card (NVIDIA or ATI) and a good one too.
Sorry to dissappoint you ;)

---

### Post by aljones15 on 2006-02-22
Krait, run glxinfo and see if it says
direct rendering or inderict. I have an 855gme
and it runs doom 3, quake 3 arena, and others just fine.
search for a thread entitled accelerating with the 855gme
there's instructions in side. you need to upgrade your kernel
to 686 then compile the DRI files for that intel card, but
I am assuming quake 4 is pretty intensive.

peace,
A

---

### Post by aljones15 on 2006-02-22
go here:

[http://www.ubuntuforums.org/showthread.php?t=132908&highlight=855gme]("http://www.ubuntuforums.org/showthread.php?t=132908&highlight=855gme")

make sure though that you're not already running direct render. quake 4 has yet to work for me regardless, but as the posters suggest it's probably really slow anyway.

peace,
A

---

### Post by aljones15 on 2006-02-22
also quake 4 is recommend for p4 or higher. I read in a forum that q4 will run in low specs on a celron 2 gighertz, but this being linux and you w/o an ati or nvidia who knows.

-
A

---

