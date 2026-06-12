---
title: "Quake4 Problems - si_code 1"
date: 2005-10-31
forum: Gaming &amp; Leisure
---

### Post by mortan on 2005-10-31
Hi folks, 

sorry, when there already was similar question, but i didn't found any. 
I installed my Quake4, symlinked the huge .pak4 files from my windows partition and tried to start the game. i need to start with sudo, because of the symlinked files (only root has access to them). Here is the log. Any hints?! .. best regards, Stefan

1 mortan@curitiba:~/quake4$ sudo ./quake4
 2 Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
 3 found interface lo - loopback
 4 found interface eth1 - 192.168.80.203/255.255.255.0
 5 CPU: Intel CPU with MMX & SSE & SSE2
 6 enabled Flush-To-Zero mode
 7 --------- Initializing File System ----------
 8 Loaded pk4 /home/mortan/quake4/q4base/game000.pk4 with checksum 0x9321cee4
 9 Loaded pk4 /home/mortan/quake4/q4base/game100.pk4 with checksum 0x6f346a2
10 Loaded pk4 /home/mortan/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
11 Loaded pk4 /home/mortan/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
12 Loaded pk4 /home/mortan/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
13 Loaded pk4 /home/mortan/quake4/q4base/pak004.pk4 with checksum 0x385aa578
14 Loaded pk4 /home/mortan/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
15 Loaded pk4 /home/mortan/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
16 Loaded pk4 /home/mortan/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
17 Loaded pk4 /home/mortan/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
18 Loaded pk4 /home/mortan/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
19 Loaded pk4 /home/mortan/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
20 Loaded pk4 /home/mortan/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
21 Loaded pk4 /home/mortan/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
22 Current search path:
23 /home/mortan/.quake4/q4base
24 /home/mortan/quake4/q4base
25 /home/mortan/quake4/q4base/pak012.pk4 (1081 files)
26 /home/mortan/quake4/q4base/pak011.pk4 (5620 files)
27 /home/mortan/quake4/q4base/pak010.pk4 (5539 files)
28 /home/mortan/quake4/q4base/pak009.pk4 (1284 files)
29 /home/mortan/quake4/q4base/pak008.pk4 (1289 files)
30 /home/mortan/quake4/q4base/pak007.pk4 (1330 files)
31 /home/mortan/quake4/q4base/pak006.pk4 (1343 files)
32 /home/mortan/quake4/q4base/pak005.pk4 (1395 files)
33 /home/mortan/quake4/q4base/pak004.pk4 (2249 files)
34 /home/mortan/quake4/q4base/pak003.pk4 (1281 files)
35 /home/mortan/quake4/q4base/pak002.pk4 (313 files)
36 /home/mortan/quake4/q4base/pak001.pk4 (5837 files)
37 /home/mortan/quake4/q4base/game100.pk4 (2 files)
38 /home/mortan/quake4/q4base/game000.pk4 (2 files)
39 game DLL: 0x0 in pak: 0x0
40 Addon pk4s:
41 file system initialized.
42 ---------------------------------------------
43 ------------ Initializing Decls -------------
44 Loading guides.... 59 loaded
45 303ms to load 1071k of material
46 104ms to load 43k of skin
47 189ms to load 716k of sound
48 28ms to load 1k of materialType
49 360ms to load 2078k of lipSync
50 113ms to load 105k of playback
51 1116ms to load 1665k of effect
52 ---------------------------------------------
53 -------- Initializing renderSystem ----------
54 using ARB renderSystem
55 renderSystem initialized.
56 ---------------------------------------------
57 Found default language English with VO
58 Couldn't open journal files
59 execing default.cfg
60 couldn't exec editor.cfg
61 couldn't exec Quake4Config.cfg
62 couldn't exec autoexec.cfg
63 WARNING: Unknown string id #str_104346
64 -------- Initializing Sound System ----------
65 sound system initialized.
66 ---------------------------------------------
67 WARNING: Unknown string id #str_104347
68 WARNING: Unknown string id #str_104348
69 --------------- R_InitOpenGL ----------------
70 Initializing SDL subsystem
71 Loading GL driver 'libGL.so.1' through SDL
72 8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
73 dlopen(libasound.so.2)
74 asoundlib version: 1.0.9
75 Alsa is available
76 ------ Alsa Sound Initialization -----
77 opened Alsa PCM device default for playback
78 device buffer size: 15052 frames ( 60208 bytes )
79 allocated a mix buffer of 16384 bytes
80 --------------------------------------
81 ...using GL_ARB_multitexture
82 ...using GL_ARB_texture_env_combine
83 ...using GL_ARB_texture_cube_map
84 ...using GL_ARB_texture_env_dot3
85 ...using GL_ARB_texture_env_add
86 X..GL_ARB_texture_non_power_of_two not found
87 ...using GL_NV_blend_square
88 ...using GL_ARB_texture_compression
89 X..GL_EXT_texture_compression_s3tc not found
90 signal caught: Segmentation fault
91 si_code 1
92 Trying to exit gracefully..
93 mortan@curitiba:~/quake4$
94 
95

---

### Post by mortan on 2005-10-31
Should have given some more Infos :) 


Am trying to play on a Fujitsu Siemens Lifebook S7010. 
Centrino 1.7 Ghz; Intel 855GME Graphics Controller with Shared Memory.
But Doom 3 works well !

Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005

Greetz, Stefan

---

### Post by EDevil on 2006-07-07
I also have the same problem on Dapper.

---

