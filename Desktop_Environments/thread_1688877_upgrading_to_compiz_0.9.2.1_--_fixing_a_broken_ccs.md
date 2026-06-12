---
title: "upgrading to compiz 0.9.2.1 -- fixing a broken ccsm"
date: 2011-02-15
forum: Desktop Environments
---

### Post by Drone4four on 2011-02-15
I'm having this problem updating compiz entirely to 0.9.2.1 from 0.8.6.  I started a forum thread over a month ago in the official compiz forums, but no one has replied:
[http://forum.compiz.org/viewtopic.php?f=85&t=14629](http://forum.compiz.org/viewtopic.php?f=85&t=14629)

So I thought I'd try asking my question here in the Ubuntu forums.  Here is a copy and paste of my thread in the compiz forums:

Yesterday I followed SmSpillaz's mini guide here ( [http://smspillaz.wordpress.com/2010/11/11/ppa/](http://smspillaz.wordpress.com/2010/11/11/ppa/) ) for installing 0.9.2.1:

```

$ sudo apt-add-repository ppa:ubuntu-desktop/ppa
$ sudo apt-get update
$ sudo apt-get dist-upgrade

```

compiz-config-settings-manager doesn't work because it wasn't updated along with the other components of compiz.  See attached for a screenshot of synaptic which shows that compiz-config-settings-manager is still stuck at version 0.8.6.  When I mark that program for uninstallation it says I need to uninstall compiz-gnome 0.9.2.1.  How do I update compiz-config-settings-manager to version 0.9.2.1?

I'm running 64bit Ubuntu 10.10.

Here is the output of some useful commands SmSpillaz recommends in one of the stickys of this forum:

```

daniel@daniel-P35-S3G:~$ compiz --version
Compiz 0.9.2.1
daniel@daniel-P35-S3G:~$ X -version

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux daniel-P35-S3G 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=1094f868-3cc1-4010-93cc-49876bce277b ro splash vga=799 quiet splash
Build Date: 23 November 2010  11:54:56PM
xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
daniel@daniel-P35-S3G:~$ nvidia-settings -q NvidiaDriverVersion

  Attribute 'NvidiaDriverVersion' (daniel-P35-S3G:0.0): 173.14.28

daniel@daniel-P35-S3G:~$ cat /var/log/Xorg.0.log | grep radeon_drv.so -C 2
daniel@daniel-P35-S3G:~$ cat /var/log/Xorg.0.log | grep intel_drv.so -C 2
daniel@daniel-P35-S3G:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9600 GT/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.28
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_bindable_uniform, GL_EXT_depth_bounds_test, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, 
    GL_NV_texture_env_combine4, GL_NV_texture_expand_normal, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

```

And here is the output of compiz-check:

```

daniel@daniel-P35-S3G:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

daniel@daniel-P35-S3G:~$ 

```
Edit: If you're having difficulty seeing the specific entries in Synaptic in the attached image, the attachment in my thread on the compiz forums is more clear.  See my first paragraph for a link to that thread.

---

### Post by lostalot on 2011-02-19
Interesting.  I've just done the same thing.  I was doing the compiz upgrade trying to install all the unsupported plugins and now I have a 'broken' desktop effects.  Desktop effects can't be enabled.  I'd listen to any ideas on this as well...

---

### Post by Drone4four on 2011-03-17
With synaptic I removed compiz 0.9.2.1 and all related packages.  Now how do I remove the ppa repositories from my sources.list?

The repository I added at the command line 4 weeks ago was 'ppa:ubuntu-desktop/ppa' with the command smspillaz recommended:
```
$ sudo apt-add-repository ppa:ubuntu-desktop/ppa
```

There are no traces of 'ppa' or 'ubuntu-desktop' in my sources.list.  See here:
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick universe
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```

So my question is how do I remove the ppa:ubuntu-desktop/ppa that I added?

---

### Post by elitenoobboy on 2011-04-01
Have you tried using the package "ppa-purge"? It might be useful for what you are trying to do.

---

### Post by karmila on 2011-04-01
> **elitenoobboy said:**
> Have you tried using the package "ppa-purge"? It might be useful for what you are trying to do.

I had this problem before when I tried to upgrade compiz to 0.9.x. It didnt' works.

All I did to solve the problem was using ppa-purge (ppa purge is not only remove ppa from source-list but also downgrade packages that get upgraded by the ppa).
In case you don't  have ppa-purge installed yet, you need to install it first:
```
sudo apt-get install ppa-purge
```and purge-ppa with this command
```
sudo ppa-purge [ppa-name]
```Anyway, i was using different ppa when upgrading the compiz before, it was ppa:/compiz...something. So i'm not really sure what the sudo apt-get dist-upgrade command did to your ubuntu.

---

### Post by Drone4four on 2011-04-04
Thanks elitenoobboy + karmila for your replies.  I installed ppa-purge and then entered this command:

> 
sudo ppa-purge ppa:ubuntu-desktop/ppa

That allowed me to successfully reinstall compiz that is in the default repositories.  However, I am now experiencing the missing the gtk window decorator.  I'll make a post in the appropriate compiz forum section and report back here. So thanks and kudos to you elitenoobboy and karmila for your help in purging my distro of compiz 0.9.2.1.  =D

---

### Post by Drone4four on 2011-04-04
Turns out -- all I had to do was tick the "Window Decorator" option under the "Effects" heading in ccsm.  Compiz is working almost flawlessly.  It's just a little slow.  For example, when rotating the cube from workplace to workplace or for example when moving windows from workplace to workplace via the expo plugin, it's all choppy.  Compiz slows down to 10fps in those cases.  Even scale is slow.  Therefore, next I'll try upgrading my drivers from the 170.xx to 260.xx using the official Ubuntu repos.

---

