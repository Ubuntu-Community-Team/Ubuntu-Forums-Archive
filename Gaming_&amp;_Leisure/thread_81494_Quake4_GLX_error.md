---
title: "Quake4 GLX error"
date: 2005-10-24
forum: Gaming &amp; Leisure
---

### Post by the__collector on 2005-10-24
Sorry if this is a total newby question but how do I solve this?

```

luc@Luc:~/quake4$ sh quake4
Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth1 - 192.168.2.3/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/luc/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /home/luc/quake4/q4base/game100.pk4 with checksum 0x6f346a2
Loaded pk4 /home/luc/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /home/luc/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/luc/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/luc/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/luc/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/luc/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/luc/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/luc/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/luc/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/luc/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/luc/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/luc/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/luc/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/luc/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /home/luc/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /home/luc/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/luc/.quake4/q4base
/home/luc/quake4/q4base
/home/luc/quake4/q4base/zpak_spanish.pk4 (3542 files)
/home/luc/quake4/q4base/zpak_italian.pk4 (3500 files)
/home/luc/quake4/q4base/zpak_french.pk4 (3462 files)
/home/luc/quake4/q4base/zpak_english.pk4 (3457 files)
/home/luc/quake4/q4base/pak012.pk4 (1081 files)
/home/luc/quake4/q4base/pak011.pk4 (5620 files)
/home/luc/quake4/q4base/pak010.pk4 (5539 files)
/home/luc/quake4/q4base/pak009.pk4 (1284 files)
/home/luc/quake4/q4base/pak008.pk4 (1289 files)
/home/luc/quake4/q4base/pak007.pk4 (1330 files)
/home/luc/quake4/q4base/pak006.pk4 (1343 files)
/home/luc/quake4/q4base/pak005.pk4 (1395 files)
/home/luc/quake4/q4base/pak004.pk4 (2249 files)
/home/luc/quake4/q4base/pak003.pk4 (1281 files)
/home/luc/quake4/q4base/pak002.pk4 (313 files)
/home/luc/quake4/q4base/pak001.pk4 (5837 files)
/home/luc/quake4/q4base/game100.pk4 (2 files)
/home/luc/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 59 loaded
432ms to load 1071k of material
140ms to load 43k of skin
254ms to load 716k of sound
37ms to load 1k of materialType
408ms to load 2078k of lipSync
135ms to load 105k of playback
1411ms to load 1665k of effect
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
TODO: Sys_SetClipboardData
********************
ERROR: SDL_SetVideoMode failed: Couldn't find matching GLX visual
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_SetVideoMode failed: Couldn't find matching GLX visual

```

---

### Post by Drakx on 2005-10-24
Have you installed SDL and your video cards 3D drivers ?

---

### Post by dmn_clown on 2005-10-24
[QUOTE=Drakx]Have you installed SDL and your video cards 3D drivers ?[/QUOTE]

You need a version of libSDL that is configured for use with X11 graphics and sound.

libsdl1.2debian-alsa*.deb works.

---

### Post by the__collector on 2005-10-25
Did that!

Now the game starts but stops returning the following in terminal:

```

luc@Luc:~/quake4$ sh quake4
Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth1 - 192.168.2.3/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/luc/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /home/luc/quake4/q4base/game100.pk4 with checksum 0x6f346a2
Loaded pk4 /home/luc/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /home/luc/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/luc/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/luc/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/luc/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/luc/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/luc/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/luc/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/luc/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/luc/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/luc/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/luc/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/luc/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/luc/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /home/luc/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /home/luc/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/luc/.quake4/q4base
/home/luc/quake4/q4base
/home/luc/quake4/q4base/zpak_spanish.pk4 (3542 files)
/home/luc/quake4/q4base/zpak_italian.pk4 (3500 files)
/home/luc/quake4/q4base/zpak_french.pk4 (3462 files)
/home/luc/quake4/q4base/zpak_english.pk4 (3457 files)
/home/luc/quake4/q4base/pak012.pk4 (1081 files)
/home/luc/quake4/q4base/pak011.pk4 (5620 files)
/home/luc/quake4/q4base/pak010.pk4 (5539 files)
/home/luc/quake4/q4base/pak009.pk4 (1284 files)
/home/luc/quake4/q4base/pak008.pk4 (1289 files)
/home/luc/quake4/q4base/pak007.pk4 (1330 files)
/home/luc/quake4/q4base/pak006.pk4 (1343 files)
/home/luc/quake4/q4base/pak005.pk4 (1395 files)
/home/luc/quake4/q4base/pak004.pk4 (2249 files)
/home/luc/quake4/q4base/pak003.pk4 (1281 files)
/home/luc/quake4/q4base/pak002.pk4 (313 files)
/home/luc/quake4/q4base/pak001.pk4 (5837 files)
/home/luc/quake4/q4base/game100.pk4 (2 files)
/home/luc/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 59 loaded
733ms to load 1071k of material
214ms to load 43k of skin
367ms to load 716k of sound
18ms to load 1k of materialType
456ms to load 2078k of lipSync
133ms to load 105k of playback
1358ms to load 1665k of effect
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
...using GL_NV_float_buffer
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using NV_vertex_program
...using NV_fragment_program
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_ARB_shader_objects
...using GL_ARB_fragment_shader
...using GL_ARB_vertex_shader
...using GL_ARB_shading_language_100
X..EXT_depth_bounds_test not found
---------------- R_NV20_Init ----------------
---------------------------------------------
----------------- R200_Init -----------------
Not available.
---------------- R_ARB2_Init ----------------
Available.
---------------------------------------------
------------ R_ReloadARBPrograms ------------
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/SimpleInteraction.vfp
glprogs/SimpleInteraction.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt
glprogs/arbFP_glasswarp.txt
glprogs/arbVP_depth.vp
glprogs/arbFP_depth.fp
glprogs/arbFP_depth_coc.fp
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
found DLL in pak file: /home/luc/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/luc/.quake4/q4base/gamex86.so
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
quake4: line 6: 14557 Segmentation fault      ./quake4.x86 $*


```

---

### Post by dmn_clown on 2005-10-26
Did you run ldconfig after installation?

```
sudo ldconfig -v
```

---

### Post by BLTicklemonster on 2005-10-26
Lmao, I just got it, but I'm afraid to attempt it in Ubuntu "yet".

---

### Post by penkoad on 2005-11-06
Hi,
> The_collector : Did you find a way to solve your problem ? 
> Sys_Error: SDL_SetVideoMode failed: Couldn't find matching GLX visual
Because I have exactly the same.
I did what were said in the thread but it still not works... :( 
I've got a Geforce 5200 with nvidia drivers (quake3 works fine but sound problems) that doesn't appear to have any problem of config...
:confused:

---

### Post by fullbanner on 2006-07-03
[QUOTE=penkoad]Hi,
> The_collector : Did you find a way to solve your problem ? 

Because I have exactly the same.
I did what were said in the thread but it still not works... :( 
I've got a Geforce 5200 with nvidia drivers (quake3 works fine but sound problems) that doesn't appear to have any problem of config...
:confused:[/QUOTE]


try changing

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth   16

to

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth   24

and add the section

SubSection     "Display"
        Viewport    0 0
        Depth       24
     Modes "1280x1024" "1280x800" "1024x768" "1024x640" "800x600" "640x480"

this is mine, put it exatly the one Deph 16

this is file /etc/X11/xorg.conf

Works with me ;)

---

### Post by Silent_Hunter on 2007-10-10
> **fullbanner said:**
> try changing

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth   16

to

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth   24

and add the section

SubSection     "Display"
        Viewport    0 0
        Depth       24
     Modes "1280x1024" "1280x800" "1024x768" "1024x640" "800x600" "640x480"

this is mine, put it exatly the one Deph 16

this is file /etc/X11/xorg.conf

Works with me ;)

I do not understand your instructions. Could you please clarify? What is the problem with my xorg.conf?

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:17 PDT 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Jun 13 16:54:50 PDT 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"

	# path to defoma fonts
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "ViewSonic"
    ModelName      "G810-3"
    HorizSync       30.0 - 97.0
    VertRefresh     50.0 - 180.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1600x1200_75 +0+0; CRT: 1600x1200 +0+0; CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"
    Option         "Coolbits" "1"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by rajeev1204 on 2007-10-10
Hi

I had a similar problem and deleting the .quake4 directory in hidden files solved it for me

---

### Post by Silent_Hunter on 2007-10-11
> **rajeev1204 said:**
> Hi

I had a similar problem and deleting the .quake4 directory in hidden files solved it for me

That worked for me also. Thanks.

---

### Post by Biznarie on 2008-04-02
I had the same error, this worked for me. Rename Quake4Config.cfg in the /home/username/.quake4/q4base directory. WARNING: The game will go back to default settings.

---

### Post by TokenBad on 2008-12-05
> **Biznarie said:**
> I had the same error, this worked for me. Rename Quake4Config.cfg in the /home/username/.quake4/q4base directory. WARNING: The game will go back to default settings.

Just a question for you guys...did you set your antialiasing?  I set mine and soon as I did the game quit working...I then had to go into the quake4config.cfg and reset the antialiasing to 0.

TokenBad

---

### Post by lzap on 2009-08-05
No need to delete whole .quake4 dir!

Just edit Quake4Config.cfg and delete all these lines:

seta image_*
seta r_*

Save and run Quake4. You have to do your video configuration again.

---

### Post by Virus666 on 2011-03-04
</div>

---

