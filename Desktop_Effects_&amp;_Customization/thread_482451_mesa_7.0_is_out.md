---
title: "mesa 7.0 is out"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by bittergourd on 2007-06-23
mesa 7.0 is released yesterday, and i tried it...

the compilation went smoothly, i got the drivers and library files as expected.  cp to /usr/lib and /usr/lib/dri, and my dri in glxinfo says no.

then i tried the driver itself (r300 and radeon, for my r9600 pro card in my case), but not the openGL library, dri is on, and mesa version is 7.0

> name of display: :0.0
disabling 3D acceleration
display: :0  screen: 0
[COLOR="Red"]direct rendering: Yes[/COLOR]
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX+/3DNow!+/SSE2 TCL
[COLOR="Red"]OpenGL version string: 1.3 Mesa 7.0[/COLOR]
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


i tried blur effect in beryl, which is buggy in mesa 6.5.2 driver, it displays correctly under mesa 7. however, the performance is still much slow than fglrx + xgl.  anyways, the new driver works ---

but not the openGL library...

btw, i tried googleearth in beryl.  it's able to start, it runs at normal speed, but very unstable (quits randomly seconds after start)

anybody else want to try it as well?

-e

---

### Post by Kazade on 2007-06-24
I'm trying to install the new mesa libraries using checkinstall (so that I can remove them if I want) but I'm having problems.

The libs compiled fine, but when I try to install it says that the files are part of the libgl1-mesa package. If I try to remove that package to make way for the new one it tries to remove ubuntu-desktop and xorg....

How can I tell apt that this package is a replacement?

---

### Post by Kazade on 2007-06-24
OK, I copied the files manually like you did, but I get no DRI, it says mesa 7.0 though what do I have to do to get DRI back?

---

### Post by bittergourd on 2007-06-24
i cant get the new libGL*, the main openGL files, to work with dri either.  so now i have that weird combination of openGL 6.5.2 and mesa driver 7.  not sure if it's totally fine, but beryl 2.0.0 and 3.0 all worked (with the slow blur and water effect that are reported to be buggy under mesa 6.5.2 driver but solved since 6.5.3).  

if you don't have your old openGL backup, im afraid that you will need to compile the old version mesa to get those files.

now trying compiz fusion...

---

### Post by rivera151 on 2007-06-24
I tried the r300 driver on my Radeon XPRESS 200m.  Direct rendering does not work still on this card.  From the developer's talk, it seems this might no be so for long.  That would be great; to dump this crappy fglrx. . .

---

### Post by bittergourd on 2007-06-24
would you choose fglrx if someday it supports aiglx? :p

---

### Post by fuoco on 2007-06-25
I don't really know much and I also couldn't yet compile mesa myself, but isn't mesa 7.0 now supposed to have the from_pixmap extension? it doesn't seem any different than what i have on my 6.5.3 mesa here...

---

### Post by r4idei on 2007-06-25
I compiled and installed correctly but when i start compiz fusion i get a blank screen :(
glxinfo says direct rendering is enabled and displayes correct version.

What can i do?

---

### Post by grazzt on 2007-06-27
Ive compiled it, copied the libGL and *_dri.so files to appropriate replaces, rebooted (to be safe?) and now I get no direct rendering, and a huge slowdown.

glxgears is about 1/3rd of what I was getting originally.

quake3 is now unplayable.

X800 card (r428 I believe, based on r300 driver) on amd 3200.

Good thing I backed up the libGL and dri files.

Dunno if I did anything wrong, heres hoping a deb comes out or something that is correct.

edit: fixed it by copying r300_dri.so to /usr/X11R6/lib/modules/dri  .. that re enabled direct rendering, and everything seems fine now.

---

### Post by Icarosaurus on 2007-07-08
I'm compiling Mesa 7.x with drm successfully since weeks using git.
I had to pay a little attention on documentation :)

EDIT: Maybe you have problems with dri 'cause new mesa needs a new version of drm (it's not included in the mesa package).
So it should be sufficient to compile drm only from git and install mesa 7.0 tarball,

This is a little quick guide:

**1)** Download drm from git
```
git clone git://anongit.freedesktop.org/git/mesa/drm
```
**2)** Compile and install drm:
in the drm directory:
```

./autogen.sh
./configure prefix=/usr
make
sudo make install

```

**3)** Download Mesa from git:
```

git clone git://anongit.freedesktop.org/git/mesa/mesa

```
**4)**Customize installation of mesa:
into the mesa directory:
```

gedit ./configs/default

```
go to the end of file and find:

```
# Installation directories (for make install)
INSTALL_DIR = /usr/local
DRI_DRIVER_INSTALL_DIR = /usr/X11R6/lib/modules/dri

```

Make it look like this:

```
# Installation directories (for make install)
#INSTALL_DIR = /usr/local
INSTALL_DIR = /usr
#DRI_DRIVER_INSTALL_DIR = /usr/X11R6/lib/modules/dri
DRI_DRIVER_INSTALL_DIR = /usr/lib/dri

```

**5)** if you want to compile only for your chipset, saving a lot of time (thanks to Meister_Eder for this hint):
```
gedit ./configs/linux-dri-x86

```
and add the line suitable for your chipset
```

DRI_DIRS = r300

```
Obviously r300 works for my card and this step is not mandatory: compiling all chipsets works if you don't know which is your chipset :).
You can check the available drivers e.g. looking for the DRI_DIRS flag into ./configs/linux-dri.

**6)** Compile and install mesa:
in the mesa directory:
```

make linux-dri-x86
sudo make install

```

**7)**If some error appears during compilation, probably you have to install some library from repositories..check for error output. 

**8 )**check now:
```
glxinfo|grep version
```
you should see Mesa 7.x

**9)**You can update drm and mesa by giving in each directory:
```

git pull origin

```
for recompiling drm:
```

make clean
make
sudo make install

```
for recompiling mesa:
```

make realclean
make linux-dri-x86
sudo make install

```

Worked fine for me under Feisty 7.04. Hope this can help!
Regards!

---

