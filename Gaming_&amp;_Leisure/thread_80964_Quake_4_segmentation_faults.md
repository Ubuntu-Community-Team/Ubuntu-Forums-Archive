---
title: "Quake 4 segmentation faults"
date: 2005-10-23
forum: Gaming &amp; Leisure
---

### Post by fimbulvetr on 2005-10-23
Hey guys, I'm getting this error:

```

Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth0 - 192.168.2.129/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/danv/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /home/danv/quake4/q4base/game100.pk4 with checksum 0x6f346a2
Loaded pk4 /home/danv/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /home/danv/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/danv/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/danv/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/danv/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/danv/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/danv/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/danv/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/danv/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/danv/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/danv/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/danv/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/danv/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/danv/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /home/danv/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /home/danv/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/danv/.quake4/q4base
/home/danv/quake4/q4base
/home/danv/quake4/q4base/zpak_spanish.pk4 (3542 files)
/home/danv/quake4/q4base/zpak_italian.pk4 (3500 files)
/home/danv/quake4/q4base/zpak_french.pk4 (3462 files)
/home/danv/quake4/q4base/zpak_english.pk4 (3457 files)
/home/danv/quake4/q4base/pak012.pk4 (1081 files)
/home/danv/quake4/q4base/pak011.pk4 (5620 files)
/home/danv/quake4/q4base/pak010.pk4 (5539 files)
/home/danv/quake4/q4base/pak009.pk4 (1284 files)
/home/danv/quake4/q4base/pak008.pk4 (1289 files)
/home/danv/quake4/q4base/pak007.pk4 (1330 files)
/home/danv/quake4/q4base/pak006.pk4 (1343 files)
/home/danv/quake4/q4base/pak005.pk4 (1395 files)
/home/danv/quake4/q4base/pak004.pk4 (2249 files)
/home/danv/quake4/q4base/pak003.pk4 (1281 files)
/home/danv/quake4/q4base/pak002.pk4 (313 files)
/home/danv/quake4/q4base/pak001.pk4 (5837 files)
/home/danv/quake4/q4base/game100.pk4 (2 files)
/home/danv/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 59 loaded
622ms to load 1071k of material
858ms to load 43k of skin
290ms to load 716k of sound
84ms to load 1k of materialType
562ms to load 2078k of lipSync
358ms to load 105k of playback
5842ms to load 1665k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
632 strings read from strings/english_code.lang
1654 strings read from strings/english_guis.lang
5616 strings read from strings/english_lips.lang
6085 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
6085 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
6085 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
6085 strings read from strings/spanish_maps.lang
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
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 8.000000
...using GL_1.4_texture_lod_bias
...using GL_EXT_shared_texture_palette
...using GL_EXT_draw_range_elements
...using GL_EXT_blend_minmax
X..GL_NV_float_buffer not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using NV_vertex_program
X..NV_fragment_program not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
X..GL_ARB_fragment_program not found
...using GL_ARB_shader_objects
X..GL_ARB_fragment_shader not found
X..EXT_depth_bounds_test not found
---------------- R_NV20_Init ----------------
---------------------------------------------
----------------- R200_Init -----------------
Not available.
---------------- R_ARB2_Init ----------------
Not available.
------------ R_ReloadARBPrograms ------------
glprogs/test.vfp
GL_PROGRAM_ERROR_STRING_ARB: line 66, column 22:  error: invalid texture coordinate reference
line 67, column 22:  error: invalid texture coordinate reference
line 68, column 22:  error: invalid texture coordinate reference
line 71, column 22:  error: invalid texture coordinate reference
line 72, column 22:  error: invalid texture coordinate reference
line 73, column 22:  error: invalid texture coordinate reference
line 79, column 22:  error: invalid texture coordinate reference
line 80, column 22:  error: invalid texture coordinate reference
line 81, column 22:  error: invalid texture coordinate reference

error at 1899:
4], defaultTexCoord;
DP4             result.texcoord[4].x, vertex.attrib[8], program.env[12];
DP4             result.texcoord[4].y, vertex.attrib[8], program.env[13];

# textures 5 takes the base coordinates by the texture matrix
MOV             result.texcoord[5], defaultTexCoord;
DP4             result.texcoord[5].x, vertex.attrib[8], program.env[14];
DP4             result.texcoord[5].y, vertex.attrib[8], program.env[15];

# calculate vector to viewer in R0
SUB             R0, program.env[5], vertex.position;

# put into texture space for TEX6
DP3             result.texcoord[6].x, vertex.attrib[9], R0;
DP3             result.texcoord[6].y, vertex.attrib[10], R0;
DP3             result.texcoord[6].z, vertex.attrib[11], R0;

# generate the vertex color, which can be 1.0, color, or 1.0 - color
# for 1.0 : env[16] = 0, env[17] = 1
# for color : env[16] = 1, env[17] = 0
# for 1.0-color : env[16] = -1, env[17] = 1
MAD             result.color, vertex.color, program.env[16], program.env[17];
#SWZ            result.color, R0, 1, 1, 1, 1;

ENDglprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp
GL_PROGRAM_ERROR_STRING_ARB: line 65, column 22:  error: invalid texture coordinate reference
line 66, column 22:  error: invalid texture coordinate reference
line 69, column 22:  error: invalid texture coordinate reference
line 70, column 22:  error: invalid texture coordinate reference
line 90, column 22:  error: invalid texture coordinate reference
line 91, column 22:  error: invalid texture coordinate reference
line 92, column 22:  error: invalid texture coordinate reference

error at 1856:
4].x, vertex.attrib[8], program.env[12];
DP4             result.texcoord[4].y, vertex.attrib[8], program.env[13];

# textures 5 takes the base coordinates by the texture matrix
DP4             result.texcoord[5].x, vertex.attrib[8], program.env[14];
DP4             result.texcoord[5].y, vertex.attrib[8], program.env[15];

# texture 6's texcoords will be the halfangle in texture space

# calculate normalized vector to light in R0
SUB             R0, program.env[4], vertex.position;
DP3             R1, R0, R0;
RSQ             R1, R1.x;
MUL             R0, R0, R1.x;

# calculate normalized vector to viewer in R1
SUB             R1, program.env[5], vertex.position;
DP3             R2, R1, R1;
RSQ             R2, R2.x;
MUL             R1, R1, R2.x;

# add together to become the half angle vector in object space (non-normalized)
ADD             R0, R0, R1;

# put into texture space
DP3             result.texcoord[6].x, vertex.attrib[9], R0;
DP3             result.texcoord[6].y, vertex.attrib[10], R0;
DP3             result.texcoord[6].z, vertex.attrib[11], R0;

# generate the vertex color, which can be 1.0, color, or 1.0 - color
# for 1.0 : env[16] = 0, env[17] = 1
# for color : env[16] = 1, env[17] = 0
# for 1.0-color : env[16] = -1, env[17] = 1
#MAD            result.color, vertex.color, program.env[16], program.env[17];
MAD             result.color, vertex.color, program.env[16].x, program.env[16].y;

ENDglprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp
GL_PROGRAM_ERROR_STRING_ARB: line 40, column 22:  error: invalid texture coordinate reference
line 45, column 22:  error: invalid texture coordinate reference
line 50, column 22:  error: invalid texture coordinate reference

error at 1202:
4].x, vertex.attrib[9], program.env[8];

# texture 3 gets the transformed tangent
DP3             result.texcoord[2].y, vertex.attrib[10], program.env[6];
DP3             result.texcoord[3].y, vertex.attrib[10], program.env[7];
DP3             result.texcoord[4].y, vertex.attrib[10], program.env[8];

# texture 4 gets the transformed tangent
DP3             result.texcoord[2].z, vertex.normal, program.env[6];
DP3             result.texcoord[3].z, vertex.normal, program.env[7];
DP3             result.texcoord[4].z, vertex.normal,program.env[8];

MOV             result.color, vertex.color;

ENDglprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp
GL_PROGRAM_ERROR_STRING_ARB: line 74, column 22:  error: invalid texture coordinate reference
line 75, column 22:  error: invalid texture coordinate reference
line 76, column 22:  error: invalid texture coordinate reference
line 79, column 22:  error: invalid texture coordinate reference
line 80, column 22:  error: invalid texture coordinate reference
line 81, column 22:  error: invalid texture coordinate reference
line 84, column 22:  error: invalid texture coordinate reference
line 85, column 22:  error: invalid texture coordinate reference
line 86, column 22:  error: invalid texture coordinate reference

error at 2311:
4].x, vertex.attrib[9], program.env[20];
DP3             result.texcoord[4].y, vertex.attrib[10], program.env[20];
DP3             result.texcoord[4].z, vertex.attrib[11], program.env[20];

# put into texture space
DP3             result.texcoord[5].x, vertex.attrib[9], program.env[21];
DP3             result.texcoord[5].y, vertex.attrib[10], program.env[21];
DP3             result.texcoord[5].z, vertex.attrib[11], program.env[21];

# put into texture space
DP3             result.texcoord[6].x, vertex.attrib[9], program.env[22];
DP3             result.texcoord[6].y, vertex.attrib[10], program.env[22];
DP3             result.texcoord[6].z, vertex.attrib[11], program.env[22];

# generate the vertex color, which can be 1.0, color, or 1.0 - color
# for 1.0 : env[16] = 0, env[17] = 1
# for color : env[16] = 1, env[17] = 0
# for 1.0-color : env[16] = -1, env[17] = 1
MAD             result.color, vertex.color, program.env[16], program.env[17];

ENDglprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/SimpleInteraction.vfp
glprogs/SimpleInteraction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp
glprogs/R200_interaction.vp
GL_PROGRAM_ERROR_STRING_ARB: line 83, column 22:  error: invalid texture coordinate reference
line 84, column 22:  error: invalid texture coordinate reference
line 85, column 22:  error: invalid texture coordinate reference
line 88, column 22:  error: invalid texture coordinate reference
line 89, column 22:  error: invalid texture coordinate reference
line 90, column 22:  error: invalid texture coordinate reference

error at 2579:
4].x, vertex.texcoord[1], R0;
DP3             result.texcoord[4].y, vertex.texcoord[2], R0;
DP3             result.texcoord[4].z, vertex.texcoord[3], R0;

# texture 5's texcoords will be the unnormalized lightDir in tangent space
DP3             result.texcoord[5].x, vertex.texcoord[1], lightDir;
DP3             result.texcoord[5].y, vertex.texcoord[2], lightDir;
DP3             result.texcoord[5].z, vertex.texcoord[3], lightDir;

# generate the vertex color, which can be 1.0, color, or 1.0 - color
# for 1.0 : env[16] = 0, env[17] = 1
# for color : env[16] = 1, env[17] = 0
# for 1.0-color : env[16] = -1, env[17] = 1
MAD             result.color, vertex.color, program.env[16], program.env[17];

ENDglprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/arbVP_glasswarp.txt
glprogs/arbFP_glasswarp.txt: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/arbVP_depth.vp
glprogs/arbFP_depth.fp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/arbFP_depth_coc.fp: GL_FRAGMENT_PROGRAM_ARB not available
---------------------------------------------
using ARB_vertex_buffer_object memory
using NV20 renderSystem
reloading textures/common/debuggraph.
reloading makeIntensity( gfx/lights/squarelight1a).
reloading gfx/lights/squarelight1.
reloading gfx/lights/round.
reloading gfx/guis/mainmenu/splash.
reloading gfx/2d/bigchars.
reloading gfx/guis/soundmeter/audiobg.
reloading gfx/guis/white.
reloading gfx/guis/guicursor_arrow.
reloading gfx/guis/guicursor_hand.
reloading gfx/guis/scrollbarh.
reloading gfx/guis/scrollbarv.
reloading gfx/guis/scrollbar_thumb.
reloading gfx/guis/scrollbar_right.
reloading gfx/guis/scrollbar_left.
reloading gfx/guis/scrollbar_up.
reloading gfx/guis/scrollbar_down.
found DLL in pak file: /home/danv/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/danv/.quake4/q4base/gamex86.so
signal caught: Segmentation fault
si_code 2
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Shutting down SDL subsystem
./quake4: line 6: 10165 Segmentation fault      ./quake4.x86 $*

```

It seems too generic for me to know exactly what's going on.
glxinfo seems fine.
glxgears works great. 


Anyone have any ideas?

---

### Post by synrat on 2005-10-23
install libslang2, libsdl1.2debian, libsdl1.2debian-oss libsd1.2-gfx in /chroot and 
add this to your quake4 start script. 


export LD_LIBRARY_PATH=/chroot/usr/lib:/chroot/lib

./quake4.x86 +set s_driver oss $*


here's an excellent walkthrough for chroot install. works just as well for breezy. 

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by stauf on 2005-10-25
Removing libsdl1.2debian-all and installing libsdl1.2debian-alsa did the trick for me - I just launch it with *quake4*. A chroot seems a little drastic.

---

