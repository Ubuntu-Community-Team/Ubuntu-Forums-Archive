---
title: "MOHAA: Run time error (SDL?)"
date: 2006-03-09
forum: Gaming &amp; Leisure
---

### Post by akiro.yamamoto on 2006-03-09
I've used the mohaa beta 3 linux installer to install mohaa to my system.
However when I try to run it I get an error about no default.cfg  :confused:  (wtf????).
So I tried copying over my config from my win :rolleyes:  (I know) install, got a little further
and then .........SDL errors??? :confused: 
Check the attatched thumbnail.....
Can anyone make some suggestions, guides or just point me in the right direction?
Because this is getting very irritating. :confused:

---

### Post by akiro.yamamoto on 2006-03-09
And this was the initial error after a fresh install.

---

### Post by akiro.yamamoto on 2006-03-09
Bump!

No One????

---

### Post by akiro.yamamoto on 2006-03-10
Well I'm using the cedega time demo right now. The only problem is the performance, but I expected to take a hit due to possible inefficiency of the
API mapping.
But at least it's running now. I will continue looking for a solution to the problems
I posted in my first post, however cedega can be used as a stop gap measure
until the native install errors are ironed out ;)

---

### Post by wolf_3d on 2006-03-10
What graphics card you got? one of those error messages means that it couldn't open your OpenGL subsystem. Its just an idea maybe its a graphics card issue.

---

### Post by akiro.yamamoto on 2006-03-10
I'm using an old Geforce2 Ti 64mb video card.
The drivers are nvidia-glx-legacy and they seem to be working properly.
Quake 2 and Torcs work just fine, the MOHAA I installed in Cedega is working
great too....
This is the output of glxinfo:
```

akiro@badger:~/quake4$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce2 GTS/AGP/SSE2
OpenGL version string: 1.5.3 NVIDIA 71.74
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette,
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fence,
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil,
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_register_combiners,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_NV_vertex_array_range,
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None

```
I will recieve a new card in a few days. I'll update this post then....

---

### Post by akiro.yamamoto on 2006-03-13
Well a little more info.
I saw a 3d card review on Anandtech.com that used MOHAA as one of the
games used as part of the review. However they used SUSE 9.2. SOOOO, I 
got my SUSE 10 cds out, installed it, installed the 7174 nvidia drivers.
Installed the mohaa beta3 (no joy), copied over my mohaa win install 
dir (no joy)  and renamed the newconfig.cfg file as default.cfg .........
..........
Voila! ;)
WTF!!??!?!!!................
MOHAA running NATIVE :) 
No WINE.......NO CEDEGA......
OH MY GOD.....

Sadly after MUCH jubilation......
I tried the same on my fav ;) distro.....
NO JOY!!!!!!
I guess there is something in all that hype about the SDL and OpenGl libs
installed as part of the Debian and derivitive distros :(

I will keep up on my research ;)

---

### Post by akiro.yamamoto on 2006-03-20
Update to my post.
Native install on SUSE 10.0 x86 runs well, however sound is a problem.
I get music and fx sound just not the sound of the radio directions like the normal
Win install.
Cedega install of mohaa gives FULL sound support :)
Of course this could be a problem with my VIA 8237 sound card........
I'm also missing speach when I play Quake IV.... I get the music... I get the+
sounds of battle.... Strogg sounds... weapons fire.... exclamations of pain .... ;)
However I get no sounds from the radio when I recieve messages from the
commander. I don't hear the team members when they speak (single player mode). It's the strangest thing......

---

### Post by akiro.yamamoto on 2006-03-20
Oh yes I should mention....
Upgraded video card from the GeForce 2 Ti 64MB to a GeForce 6200 256MB card.
Now I have to try overclocking this thing ;)
Even with this card Quake IV is a beast....
Comp: 
CPU: Cel 326 
Mem: 768 MB (PC 3200 DDR)
HD:   160 GB (7200 rpm, 16MB Cache, PATA)
Video Card: eVGA GeForce 6200 256MB

Quake IV settings needed for acceptable game play:
Resolution: 800x600 ;)
Detail level: Low  ;)
Yeah that's right.......
Now if that ain't a kick in the f@$#*!& balls ;)

---

### Post by akiro.yamamoto on 2006-03-21
Final update ;)
To get this game to run natively you need to install (at least I did) the NVidia
drivers from nvidia's website. Once you do that, the game runs without errors.
Sound is still a problem though and apparently I'm not the only one to remark
on this either. ;)
All the sounds work for me except radio transmissions and you will not normally
hear other allied personel... Example the first mission, you will not hear much
of the dialog... which sucks!!!

---

### Post by akiro.yamamoto on 2006-03-21
As my final recommendation:
Right now if you want to play this game in linux... use cedega (1st choice) or wine.
It can be used with the linux-mohaa-beta3 installer for a native install. But there 
are certain caveats. 
1) Sound may be a problem for you. (I only have 1 sound card
so I am currently unable to extensive research about this issue). 
2) If you have a NVidia Video card.. install the drivers from NVidia's website.
    Even the 7174 drivers (nvidia-glx-legacy) as there seems to be a problem  
    with the drivers that are available from the repos.

Anyway I hope this helps someone else in the future....
I will only update this if I get a new sound card or if I get a workaround for my
sound issues in the native install.
Akiro
;)

---

### Post by traxtar3 on 2007-09-09
this is not a video card problem!!

if it can't find the default.cfg file then it was never installed.

I had the same problem

here is what i did to solve the problem:

I removed all of the old install files (sudo rm -rf /usr/local/games/mohaa)
removed temp files that installer makes (sudo rm -rf /tmp)
re-made /tmp dir (sudo mkdir /tmp)
logged in as root (sudo su) or (logout and log back in as root)

NOTE: logging out and logging back in as root is a bad idea, but desperate times call for desperate measures)

cd /to/mohaa/install/file/location (cd /home/user_name/Desktop)
./mohaainstall.run

it should install it properly now, but watch the terminal and make sure that there are no errors that you need to worry about. (ignore input/output errors)

hope this helps

---

