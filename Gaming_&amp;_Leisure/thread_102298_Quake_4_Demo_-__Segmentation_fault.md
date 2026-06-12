---
title: "Quake 4 Demo -  Segmentation fault"
date: 2005-12-11
forum: Gaming &amp; Leisure
---

### Post by ninocass on 2005-12-11
im getting the following errors what i try and run the game.
```

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


```

if i cant get it working is there a set way to uninstall something?

Thanks

Nino

---

### Post by londonboi2k3 on 2005-12-12
Do you by any chance use and ATI card?

Had a problem with a game and got the same message?

---

### Post by ninocass on 2005-12-12
no i just have the onboard Graphics card im not too sure what its called

---

### Post by joshuapurcell on 2005-12-12
If you don't know what card you have then chances are the correct drivers are not installed. What type of motherboard do you have, and then someone here will be able to tell you the integrated video card that is in that motherboard most likely. Also, were you ever able to run 3D games in Windows? Are you sure the integrated card you are using is capable of 3D?

---

### Post by aljones15 on 2005-12-13
I'm having the same problem although strangely
doom 3 worked (although slowly) before on breezy before
I fucked something up.
Anyway using an XNOTE LS50a
graphics card

Intel 855GME Internal Graphics
also has an ATI Mobility
RADEON™ 9700

is that the problem?

peace,
A

---

### Post by aljones15 on 2005-12-13
ubuntu says I have the ati drivers installed:
version 6.8.2-77
do i need the fglrx installed too?

thanks,
A

---

### Post by aljones15 on 2005-12-13
added fglrx
still getting the same error.
maybe need to restart...

peace,
A

---

### Post by aljones15 on 2005-12-13
more info

andrew@ubuntu:~/quake4-demo$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess


it doesn't seem to have specifically noticed what ati card
I have yet.

thanks,
A

---

### Post by Original Brownster on 2005-12-13
Hi,
The output that says 
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

AFAIK this shows your setup is not using the ati accelerated drivers but the software drivers instead.

I'm at work otherwise I could help more, however things you can try are look  at the system devices tool to see if it gives you the name of the graphics card that has been recognised (cant remember the exact name of the tool but it's probably on the 'system' menu) then look at the ati driver howto which as part of it explains how to switch from software to hardware rendering.

Regards

---

### Post by aljones15 on 2005-12-13
hmm and ati doesn't detect a card when i run the set up.
fglrxconfig

maybe the xnote doesn't have an ati card.
who knows.

-
A

---

### Post by aljones15 on 2005-12-13
brownster:

855gm graphics device is all I can see in device manager.
think that's the intel card.
fglrx isn't picking up an accelerator either.

peace,
A

---

### Post by ninocass on 2005-12-13
oi you big thread hijacker you!!! ;) ;) ;) ;)

i have ran 3D games on windows on this system, MOHAA and BF: Vietnam

my system is:

Video Graphics: Intel&#174;  Graphics Media Accelerator 900TM  integrated graphics with up to 128MB shared system memory

and

Chipset: Intel&#174;  915GM chipset (with Intel&#174;  GMA 900TM integrated graphics)

---

### Post by aljones15 on 2005-12-13
nino,

quake 4 working for you yet though?
or are u still missing some libraries?
it looks like we're both running on software rendering through mesa.

peace,
A

---

### Post by aljones15 on 2005-12-13
ahhhh

now I find out
my computer is the low end xnote and doesn't have an ati card. sucks

[http://www.productreview.com.au/showitem.php?item_id=1398](http://www.productreview.com.au/showitem.php?item_id=1398)

so how do we get hardware rendering with an:
Intel 855GME (Intel Extreme Graphics)

is that possible?

-
A

---

### Post by ninocass on 2005-12-13
i couldnt be bothered messing with it as its only a demo so i just deleted the whole thing!!!

i have Americas Army downloading at the minute ill let you know how that goes

Nino

---

### Post by akiro.yamamoto on 2006-03-20
Quake 4 is a beast when it comes to requirements for game play...
You will need a Nvidia FX 5600 128mb GT card at least for acceptable play.
That is if you meet the other requirements ;)

---

### Post by Konami on 2007-06-09
> **ninocass said:**
> im getting the following errors what i try and run the game.
X..GL_EXT_texture_compression_s3tc not found
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..

[/code]

if i cant get it working is there a set way to uninstall something?

Thanks

Nino

I too have a segmentation fault but is not the graphic rendering and ****... it has to do with some commands sent to memory or something because I run a server that is console only and the console gets the segmentation fault error too!:(

---

