---
title: "the well known prob ET and TS :("
date: 2005-11-20
forum: Gaming &amp; Leisure
---

### Post by Soki on 2005-11-20
Hi Ubuntu friends

First i gotta say that I have already found lots of solutions to the problem, but not one of it worx for me. Although I gotta say that I am bloody new on linux and all that stuff... so please be patient if I am just dumb and dumber at the moment :D
I am very thankfull for anyone who trys to help a complete linux n00b... 

:thankyou:

Its about the well known problem " ET and TS2 "
like this:

/dev/dsp: Device or resource busy
Could not open /dev/dsp


Hardware:
amd 2600+
Asus A7N8X-X
sound ac97 onboard


What I tried yet:



#echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
#echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
.....didnt work
_________________________________________________________________________
#ps -A | grep esd
...nothing
_________________________________________________________________________
#killall esd ; killall -9 esd; et
...nothing
_________________________________________________________________________
#id | grep audio
...yes I am in the group "audio"
_________________________________________________________________________
> changing snd device in etconfig.cfg to: seta snddevice "/dev/adsp"
... doesnt work ... ( made it /dev/dsp again )
_________________________________________________________________________
> in ET console: set +snddevice /dev/dsp
...didnt work
_________________________________________________________________________
#artsdsp -m et
... didnt work
_________________________________________________________________________
#sudo gedit /etc/esound/esd.conf
like this:
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

...didnt work... although tried "mixer" and "default"
_________________________________________________________________________


# lsof /dev/dsp

comes out:

COMMAND    PID USER   FD   TYPE DEVICE SIZE NODE NAME
TeamSpeak 9123 soki   22u   CHR   14,3      7284 /dev/dsp
_________________________________________________________________________

#lsof /dev/snd/* 

comes out:

nothing

_________________________________________________________________________


--- Checked my loud speakers...they are properly plugged in, etc... :D omg

_________________________________________________________________________

--- Volume Settings checked... should blast away my ears :D

_________________________________________________________________________

#sudo apt-get install libesd-alsa0

...already installed

_________________________________________________________________________

#sudo gedit /etc/asound.conf

made this file like this:

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
periods 128
rate 44100
}
bindings {
0 0
1 1
}
}


nothing after restarting alsa :/
_________________________________________________________________________

That comes out after starting ET:



ET 2.55 linux-i386 May 27 2003
----- FS_Startup -----
Current search path:
/home/soki/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3729 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Sokilx/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 6800 LE/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6800 LE/AGP/SSE/3DNOW!
GL_VERSION: 2.0.0 NVIDIA 76.67
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffer s GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL _ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow G L_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_te xture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mi rrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_tr anspose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_s hader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_ mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_ble nd_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_ minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EX T_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuff er_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_pixel_buffer_obje ct GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_s eparate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stenci l_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_ EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT _texture_mirror_clamp GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_ test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region G L_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_ float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_op tion GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_mul tisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixe l_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners  GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc  GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_ar ray_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1  GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX _conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_te xture GL_SGIX_shadow GL_SUN_slice_accum
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/soki/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/soki/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/soki/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No suc h file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xade69bb4
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: SKPC1UBUNTU
IP: 192.168.0.10
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
_________________________________________________________________________
_________________________________________________________________________


...perhaps I made some things wrong... or did things which were unnecessery...

did I kill the sound by myself ??

Did I forget to post anything of interest ??

What can I do better next time I post ??

Before I start crying... and re-use Windows XP... please... pleaaase... can anybody help me ?? :confused: 

best wishes
Soki

---

### Post by Harleen on 2005-11-20
The game complains about your sound device being in use, so you have to quit the application, that occupies it. You have tested the device before, and it was in use by Teamspeak. (BTW. Thanks for the lsof-command - didn't know about it yet)
Try again after killing it.

---

### Post by Soki on 2005-11-20
...well tHx... I forgot to say that  I do need Teamspeak and ET together :D

---

### Post by Harleen on 2005-11-20
Your problem is, that your card can only be used by one application at a time. Either because your card isn't capable to handle multiple input or because the linux drivers are crap.

The easiest solution is replacing the sound card with a better one.
But there has to be a cheaper solution. And that's, what the sound servers are used for. Usually all GNOME-apps play their sound using esd, while KDE uses arts. I think there's a command, which lets an application use the soundserver. I don't use them, so I can provide only theoretical help. But your "artsdsp -m ..." command looks promising. Can you run both, Teamspeak and ET with that?

---

### Post by Soki on 2005-11-20
no that doesnt work, too... hm
but thanks for ur answer, it will help me getting a step further :smile: 

I actualy got another pci soundcard available... so ill just replace the
onboardsound.

thx,
Soki

---

### Post by ulisse on 2005-11-21
I posted a solution that worked for me, but it seems that nobody is looking at that... :( 
Take a look:
[http://ubuntuforums.org/showthread.php?t=88055](http://ubuntuforums.org/showthread.php?t=88055)

---

### Post by Soki on 2005-11-21
hey ulisse... very nice, thank you :) 

I will try that soon and will give a reply if it worked or not ;)

greetz


EDIT:

:( didnt work... hehe... no I cant even hear sound in ET when my TS2 is off Oo... weird...
I think I need to get help from one of u guys real soon !!!

---

### Post by hav0x on 2005-12-10
[http://www.ubuntuforums.org/showpost.php?p=560917&postcount=47](http://www.ubuntuforums.org/showpost.php?p=560917&postcount=47)

---

