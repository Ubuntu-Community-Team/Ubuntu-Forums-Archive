---
title: "Low FPS in true combat?"
date: 2006-04-26
forum: Gaming &amp; Leisure
---

### Post by Angry penguin on 2006-04-26
I just installed true combat:elite and I noticed that the mouse moves incredibly slow when inside the main menu, like 2-3 FPS!

I checked my glxgears:
9493 frames in 5.0 seconds = 1881.484 FPS
9462 frames in 5.0 seconds = 1888.700 FPS
9462 frames in 5.0 seconds = 1889.203 FPS

I have the nvidia drivers installed correctly, I am running an MX4000 video card at the moment and have 1GB of Kingston Hyperex ram DDR400 on an Athlon XP 2600+. Counter Strike:Source runs at a good 30FPS in my windows partition, albeit at 800x600 but, no complaints. 

Am I missing something or is my video card just too crappy to run this game?

---

### Post by minisori on 2006-04-27
I have almost your same computer with half your ram and a nvidia 6200. I can run it at 1024 with 90fps.

Maybe you dont have opengl properly installed on linux. Try glxinfo and see if its enabled.

---

### Post by Angry penguin on 2006-04-27
Output: glxinfo

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX 4000/AGP/SSE/3DNOW!
OpenGL version string: 1.2 (1.5.6 NVIDIA 87.56)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, GL_EXT_texture_env_add,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by Angry penguin on 2006-04-27
my opengl seems to be working fine, any other suggestions? My processor jumps to 100% when I launch true combat, I think thats why it seems so slow. I am all out of ideas. :(

---

### Post by Harleen on 2006-04-27
[QUOTE=Angry penguin]Output: glxinfo

name of display: :0.0
display: :0  screen: 0
[COLOR="Red"]direct rendering: No[/COLOR]
server glx vendor string: SGI
server glx version string: 1.2
[...][/QUOTE]

Your OpenGL does not seem to work correctly. Direct rendering should say "yes" and the glx vendor string looks wrong to me. It has to be "NVIDIA Corporation". The SGI stands for software rendering, I think. Are you really sure, you have installed the nvidia drivers correctly?

Does your /etc/X11/xorg.conf load the "nvidia" driver or does it still use the "nv" driver?

```
Section "Device"
        Identifier      "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
        Driver          "nvidia"
        [...]
EndSection

```

---

### Post by Angry penguin on 2006-04-27
the nvidia splash screen appears after login signifying a successful install of the nvidia drivers.

xorg:
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
        BusID           "PCI:2:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 
       #Option "NvAGP" "0"
       #Option "IgnoreDisplayDevices" "DFP,TV"
       # Option "NoRenderExtension" "Off"
       # Option "Render" "Enable"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Monitor        "LCD-MONITOR"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       1

---

### Post by Angry penguin on 2006-04-27
I also get an error if I try to start a server

[HTML]cannot write to hunkusage.dat[/HTML]

No clue.

---

### Post by Angry penguin on 2006-05-02
Will I get the latest nvidia drivers if I get them through apt-get? I am going to have to reinstall dapper, my xorg is completely screwed, I tried to install the latest drivers manually.

---

