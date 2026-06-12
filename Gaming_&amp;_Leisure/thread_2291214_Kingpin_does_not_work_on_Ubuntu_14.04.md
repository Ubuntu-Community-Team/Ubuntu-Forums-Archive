---
title: "Kingpin does not work on Ubuntu 14.04"
date: 2015-08-18
forum: Gaming &amp; Leisure
---

### Post by mateo14 on 2015-08-18
Hi

I tried to run Kingpin on Ubuntu 14.04 but it does not work: 

 ./kingpin.sh +set gl_mode 3
KPHack 0.0.5: DGA mouse enabled; FullScreen enabled.
Added packfile ./main/pak0.pak (456 files)
execing default.cfg
couldn't exec config.cfg
couldn't exec linux.cfg
Console initialized.

------- sound initialization -------
/dev/dsp: Input/output error
Could not open /dev/dsp
------- Loading ref_glx.so -------
ref_gl version: GL 0.01
R_SetMode() - CDS not allowed with this driver
Initializing OpenGL display
...setting mode 3: 1024 768
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 320M/integrated/SSE2
GL_VERSION: 3.3.0 NVIDIA 340.76
GL_EXTENSIONS: GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_blend_func_extended GL_ARB_clear_buffer_object GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_separate_shader_objects GL_ARB_shader_bit_encoding GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_include GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_buffer_range GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback_instanced GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shader_integer_mix GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_shared_exponent GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode GL_EXT_texture_storage GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback2 GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_x11_sync_object GL_EXT_import_sync_object GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KHR_debug GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_copy_image GL_NV_depth_buffer_float GL_NV_depth_clamp GL_NV_ES1_1_compatibility GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_gpu_program4_1 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_parameter_buffer_object2 GL_NV_path_rendering GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_shader_buffer_load GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_multisample GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_transform_feedback2 GL_NV_vdpau_interop GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_buffer_unified_memory GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NVX_gpu_memory_info GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
Received signal 11, exiting...

I tried to use this script because it worked previously, but now I have some issues with it:

[http://liflg.org/forum/viewtopic.php?f=2&t=969&p=5497&hilit=kingpin#p5497](http://liflg.org/forum/viewtopic.php?f=2&t=969&p=5497&hilit=kingpin#p5497)

./kingpin
KPHack 0.0.5: DGA mouse enabled; FullScreen enabled.
Added packfile ./main/pak0.pak (456 files)
execing default.cfg
couldn't exec config.cfg
couldn't exec linux.cfg
Console initialized.

------- sound initialization -------
/dev/dsp: Input/output error
Could not open /dev/dsp
------- Loading ref_glx.so -------
ref_gl version: GL 0.01
R_SetMode() - CDS not allowed with this driver
Initializing OpenGL display
...setting mode 0: 640 480
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  45
  Current serial number in output stream:  46

Can you help me?

uname -a
Linux ******-Macmini 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:18:00 UTC 2015 i686 i686 i686 GNU/Linux

This is my computer:

[https://support.apple.com/kb/SP586?locale=en_US](https://support.apple.com/kb/SP586?locale=en_US)

---

### Post by radoslavfatura7 on 2015-08-19
It's an old game, you have to keep that in mind.

I've got to the menu with this script.

Create e.g. kp.sh and copy-paste this:

```
#!/bin/sh 

# Look, it's a hacky little version number so that makeupgrade.sh 
# doesn't barf: v1.06a. 


# Function to find the real directory a program resides in. 
# Feb. 17, 2000 - Sam Lantinga, Loki Entertainment Software 
FindPath() 
{ 
fullpath="`echo $1 | grep /`" 
if [ "$fullpath" = "" ]; then 
oIFS="$IFS" 
IFS=: 
for path in $PATH 
do if [ -x "$path/$1" ]; then 
if [ "$path" = "" ]; then 
path="." 
fi 
fullpath="$path/$1" 
break 
fi 
done 
IFS="$oIFS" 
fi 
if [ "$fullpath" = "" ]; then 
fullpath="$1" 
fi 
# Is the awk/ls magic portable? 
if [ -L "$fullpath" ]; then 
fullpath="`ls -l "$fullpath" | awk '{print $11}'`" 
fi 
dirname $fullpath 
} 


if [ "${KINGPIN_DATA_PATH}" = "" ]; then 
KINGPIN_DATA_PATH=`FindPath $0` 
fi 


# crap in the game like "./ref_gl.so", etc. 
LD_LIBRARY_PATH=${KINGPIN_DATA_PATH}:${LD_LIBRARY_PATH}:. 


export KINGPIN_DATA_PATH 
export LD_LIBRARY_PATH 
export KPHACK_DGAMOUSE=1 KPHACK_FULLSCREEN=1 KPHACK_WHEEL=1 
export LD_PRELOAD="${KINGPIN_DATA_PATH}/kphack.so:$LD_PRELOAD" 


if [ -x "${KINGPIN_DATA_PATH}/kingpin.x86" ]; then 
exec ${KINGPIN_DATA_PATH}/kingpin.x86 +set vid_ref glx +set gl_driver libGL.so.1 "$@" 
fi 


echo "Couldn't run Kingpin Life of Crime (kingpin.x86). Is KINGPIN_DATA_PATH set?" 
exit 1 
```

Make it executable by chmod +x kp.sh and run.
For some (security) reasons, the game needs to be owned and launched by root, keep that in mind.
It's not fully working for me like there;s no sound, crashing after New Game selected, I'll try to make it run and let you know ;)

---

### Post by mateo14 on 2015-08-19
Thanks for the answer.

Kratz00 helped me to run this game on Ubuntu 14.04:

I installed ghex and I modified the file ref_glx.so

"[COLOR=#000000][FONT=Verdana]When you start reading the Kingpin and Kingpin GL_EXTENSIONS breaks off with [/FONT][/COLOR]**Received Signal 11, exiting ... Opens the ref_glx.so with a hex editor (eg hexcurse), studied in ASCII mode by GL_EXTENSIONS and replaces the% s behind by two space (hex code 20)**"

[http://wiki.linuxgaming.de/index.php/Kingpin:_Life_of_Crime#Grafikkarte.2FTreiber_zu_neu](http://wiki.linuxgaming.de/index.php/Kingpin:_Life_of_Crime#Grafikkarte.2FTreiber_zu_neu)

Later, I had to install the package alsa-oss:

sudo apt-get install alsa-oss

I typed this command in the terminal to load the kernel module:

sudo modprobe snd-pcm-oss

I added this line: snd-pcm-oss to file: /etc/modules.

I rebooted my computer as root I typed this command:

echo 'kingpin.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss

exit

FInally, I can run this incredible classic game for Linux which was published in 1999:

cd kingpin
./kingpin.sh


Someone should prepare modified version of et-sdl-sound for the Linux version of Kingpin.

---

### Post by mastablasta on 2015-08-20
things are done so easy in Linux it seems.... :P

---

### Post by mateo14 on 2015-08-20
> **mastablasta said:**
> things are done so easy in Linux it seems.... :P

I can agree that hex editors are not applications that should be used to run old games on Linux but this method works in this case.


On the other hand, Kingpin for Linux was published 16 years ago, and I am happy that I can run this game on the modern operating system.


For example, I will have to use a really old PC if I want to run Mohaa for Linux which was published in 2004.

---

### Post by radoslavfatura7 on 2015-08-20
> **mateo14 said:**
> 
For example, I will have to use a really old PC if I want to run Mohaa for Linux which was published in 2004.

I've got MOHAA to run on my machine.

The sound is the biggest issue so far. :(

It's sad that it isn't finished.
Sorry for OT

---

### Post by mateo14 on 2015-08-20
> **radoslavfatura7 said:**
> I've got MOHAA to run on my machine.

The sound is the biggest issue so far. :(

It's sad that it isn't finished.
Sorry for OT

I noticed that Mohaa on modern distribution of Linux crashes in this place:


[https://www.youtube.com/watch?v=QK9eGUAjVTo](https://www.youtube.com/watch?v=QK9eGUAjVTo)


7:45


Later, it crashes all the time, and I did not find the solution.


It will be great if someone can modify et-sdl-sound in order to work with the Linux version of kingpin.

---

