---
title: "I really need help with the sounds"
date: 2006-12-16
forum: Gaming &amp; Leisure
---

### Post by Sambie on 2006-12-16
I'm probably being a pain in the butt for some of you guys but this is driving me nuts. I cannot get my sounds to work anymore on Wolfenstein ET. I don't remember doing anything different other than changing something totally different... which was to be able to play on the map: North pole without being kicked off of the server.

I use to be able to do the fallowing codes

1. sudo killall artsd 
2. sudo killall esd

3. sudo killall esd
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit

and it worked but now when I try to use theses codes it does not fix the problem.

Here is the log when I try to run ET on terminal.
> 
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/brittany/.etwolf/etmain/ww10.pk3 (1 files)
/home/brittany/.etwolf/etmain/whaleclient-1_4_beta1.pk3 (98 files)
/home/brittany/.etwolf/etmain/Warbell.pk3 (242 files)
/home/brittany/.etwolf/etmain/vlasterx_ss_skins_v1-0.pk3 (125 files)
/home/brittany/.etwolf/etmain/vg10.pk3 (1 files)
/home/brittany/.etwolf/etmain/vf10.pk3 (1 files)
/home/brittany/.etwolf/etmain/venice.pk3 (330 files)
/home/brittany/.etwolf/etmain/ve10.pk3 (1 files)
/home/brittany/.etwolf/etmain/vd7.pk3 (1 files)
/home/brittany/.etwolf/etmain/vd3.pk3 (1 files)
/home/brittany/.etwolf/etmain/va10.pk3 (1 files)
/home/brittany/.etwolf/etmain/ukcampaignsv4.pk3 (2 files)
/home/brittany/.etwolf/etmain/transmitter.pk3 (143 files)
/home/brittany/.etwolf/etmain/thehouse.pk3 (113 files)
/home/brittany/.etwolf/etmain/temple_final.pk3 (57 files)
/home/brittany/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/brittany/.etwolf/etmain/steelplant2.pk3 (147 files)
/home/brittany/.etwolf/etmain/sedesrc1.pk3 (77 files)
/home/brittany/.etwolf/etmain/saberpeak.pk3 (243 files)
/home/brittany/.etwolf/etmain/resurrection.pk3 (301 files)
/home/brittany/.etwolf/etmain/resurrection.e985d9bf.pk3 (305 files)
/home/brittany/.etwolf/etmain/password2_v12.pk3 (100 files)
/home/brittany/.etwolf/etmain/over_the_top.pk3 (144 files)
/home/brittany/.etwolf/etmain/northpole.pk3 (112 files)
/home/brittany/.etwolf/etmain/night_crawlers.pk3 (108 files)
/home/brittany/.etwolf/etmain/nemorosusrc1.pk3 (90 files)
/home/brittany/.etwolf/etmain/haunted_mansionb2.pk3 (77 files)
/home/brittany/.etwolf/etmain/greece6.pk3 (73 files)
/home/brittany/.etwolf/etmain/goldrush-gaw.pk3 (37 files)
/home/brittany/.etwolf/etmain/goldrush-ga.pk3 (36 files)
/home/brittany/.etwolf/etmain/fun_testing.pk3 (1 files)
/home/brittany/.etwolf/etmain/Frostbite.pk3 (99 files)
/home/brittany/.etwolf/etmain/flughafen.pk3 (355 files)
/home/brittany/.etwolf/etmain/fatal_mill_b4.pk3 (49 files)
/home/brittany/.etwolf/etmain/fall_06_part_3_fixed.pk3 (1 files)
/home/brittany/.etwolf/etmain/fall_06_part_2.pk3 (1 files)
/home/brittany/.etwolf/etmain/fall_06_part_1.pk3 (1 files)
/home/brittany/.etwolf/etmain/et_ice.pk3 (61 files)
/home/brittany/.etwolf/etmain/et_beach.pk3 (177 files)
/home/brittany/.etwolf/etmain/darji2.pk3 (220 files)
/home/brittany/.etwolf/etmain/castleattack_b3.pk3 (165 files)
/home/brittany/.etwolf/etmain/caen.pk3 (82 files)
/home/brittany/.etwolf/etmain/beta_low_mount_***.pk3 (71 files)
/home/brittany/.etwolf/etmain/bergen.pk3 (181 files)
/home/brittany/.etwolf/etmain/baserace_b3a.pk3 (139 files)
/home/brittany/.etwolf/etmain/baserace.pk3 (129 files)
/home/brittany/.etwolf/etmain/2tanks_171.pk3 (210 files)
/home/brittany/.etwolf/etmain/2hide_cal_r1.pk3 (69 files)
/home/brittany/.etwolf/etmain/1944_beach.pk3 (60 files)
/home/brittany/.etwolf/etmain
/home/brittany/enemy-territory/etmain/pak2.pk3 (22 files)
/home/brittany/enemy-territory/etmain/pak1.pk3 (10 files)
/home/brittany/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/brittany/enemy-territory/etmain/mp_bin.pk3 (6 files)
/home/brittany/enemy-territory/etmain

----------------------
8971 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Sambie/etconfig.cfg
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
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
GL_VERSION: 2.0.2 NVIDIA 87.76
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffer
s GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader
GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL
_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_p
oint_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_A
RB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_AR
B_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_text
ure_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_
texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_ver
tex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_te
xture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_
abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_
func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_a
rray GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT
_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_dept
h_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameter
s GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL
_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D G
L_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp
 GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisot
ropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_
EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL
_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_b
uffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_N
V_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragm
ent_program_option GL_NV_fragment_program2 GL_NV_gpu_program_parameters GL_NV_ha
lf_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_
query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV
_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texg
en_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_tex
ture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_sh
ader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 G
L_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_p
rogram2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_
mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_acc
um
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_
SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_
float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/brittany/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/brittany/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/brittany/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No
 such file or directory"
Sys_LoadDll(/home/brittany/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa9e00f40
Sys_LoadDll(ui) succeeded!
^1ERROR: ui/ingame_vote_misc.menu, line 59: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 59: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 60: unknown menu item keyword modStringN
ot
^1ERROR: ui/ingame_vote_misc.menu, line 60: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 64: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 64: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 65: unknown menu item keyword modStringN
ot
^1ERROR: ui/ingame_vote_misc.menu, line 65: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 83: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 83: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 94: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 95: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 99: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 99: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu item keyword modString
^1ERROR: ui/ingame_vote_misc.menu, line 100: unknown menu item keyword etpub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 59: unknown menu item keyword mo
dString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 59: unknown menu item keyword et
pub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 60: unknown menu item keyword mo
dStringNot
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 60: unknown menu item keyword et
pub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 64: unknown menu item keyword mo
dString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 64: unknown menu item keyword et
pub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 65: unknown menu item keyword mo
dStringNot
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 65: unknown menu item keyword et
pub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 83: unknown menu item keyword mo
dString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 83: unknown menu item keyword et
pub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 94: unknown menu item keyword mo
dString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 95: unknown menu item keyword et
pub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu item keyword mo
dString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 98: unknown menu item keyword et
pub
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 99: unknown menu item keyword mo
dString
^1ERROR: ui/ingame_vote_misc_refrcon.menu, line 99: unknown menu item keyword et
pub
^1ERROR: ui/whale_menu_hud.menu, line 58: unknown menu item keyword cvarInt
^1ERROR: ui/whale_menu_hud.menu, line 58: unknown menu item keyword cg_popupTime
^1ERROR: ui/whale_menu_hud.menu, line 58: unknown menu item keyword 1000
^1ERROR: ui/whale_menu_hud.menu, line 58: unknown menu item keyword 0
^1ERROR: ui/whale_menu_hud.menu, line 58: unknown menu item keyword 1500
^1ERROR: ui/whale_menu_hud.menu, line 60: unknown menu item keyword cvarInt
^1ERROR: ui/whale_menu_hud.menu, line 60: unknown menu item keyword cg_popupStay
Time
^1ERROR: ui/whale_menu_hud.menu, line 60: unknown menu item keyword 2000
^1ERROR: ui/whale_menu_hud.menu, line 60: unknown menu item keyword 0
^1ERROR: ui/whale_menu_hud.menu, line 60: unknown menu item keyword 4000
^1ERROR: ui/whale_menu_hud.menu, line 62: unknown menu item keyword cvarInt
^1ERROR: ui/whale_menu_hud.menu, line 62: unknown menu item keyword cg_popupFade
Time
^1ERROR: ui/whale_menu_hud.menu, line 62: unknown menu item keyword 2500
^1ERROR: ui/whale_menu_hud.menu, line 62: unknown menu item keyword 0
^1ERROR: ui/whale_menu_hud.menu, line 62: unknown menu item keyword 5000
^1ERROR: ui/whale_menu_hud.menu, line 69: unknown menu item keyword cvarInt
^1ERROR: ui/whale_menu_hud.menu, line 69: unknown menu item keyword cg_locationm
axchars
^1ERROR: ui/whale_menu_hud.menu, line 69: unknown menu item keyword 25
^1ERROR: ui/whale_menu_hud.menu, line 69: unknown menu item keyword 0
^1ERROR: ui/whale_menu_hud.menu, line 69: unknown menu item keyword 76
^1ERROR: ui/whale_menu_hud.menu, line 89: unknown menu item keyword cvarInt
^1ERROR: ui/whale_menu_hud.menu, line 89: unknown menu item keyword cg_hudyOffse
t
^1ERROR: ui/whale_menu_hud.menu, line 89: unknown menu item keyword 10
^1ERROR: ui/whale_menu_hud.menu, line 89: unknown menu item keyword 0
^1ERROR: ui/whale_menu_hud.menu, line 89: unknown menu item keyword 20
^1ERROR: ui/whale_menu_hud.menu, line 91: unknown menu item keyword cvarInt
^1ERROR: ui/whale_menu_hud.menu, line 91: unknown menu item keyword cg_recording                                                              _statusline
^1ERROR: ui/whale_menu_hud.menu, line 91: unknown menu item keyword 480
^1ERROR: ui/whale_menu_hud.menu, line 91: unknown menu item keyword 0
^1ERROR: ui/whale_menu_hud.menu, line 91: unknown menu item keyword 480
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: brittany-desktop
IP: [COLOR="Blue"]deleted[/COLOR]
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: Attempting to resolve master6.evenbalance.com
^5PunkBuster Client: Resolved to [COLOR="Blue"][deleted][/COLOR]
^5PunkBuster Client: PunkBuster Client (v1.286 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60 linux-i386 Mar 10 2005]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to [COLOR="Blue"]deleted[/COLOR]
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
brittany@brittany-desktop:~$


The [COLOR="Blue"]Blue[/COLOR] is what I've edited out.

A member by the name of **blackmh** mention on one of my posts

> Kill artsd before starting the game. Also, open etconfig.cfg in /home/username/.etwolf/etmain and check if it contains this line : seta snddevice "/dev/dsp"

Checked my etconfig.cfg on /.etwolf/etmain and I do notice that on seta snddevice it does have "/dev/dsp" Do I need to somehow change this? If so to what?

also what can I do to fix the 1ERROR's that I'm recieving?

---

### Post by Sambie on 2006-12-16
by the way on the terminal log...

on 

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------

It sometimes changes to 

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------

---

### Post by Sambie on 2006-12-16
bump

---

### Post by Sambie on 2006-12-18
bump..

---

### Post by shamanu on 2006-12-18
This is what i used to play RTCW with sounds (I understood it should work with ET):
1.open a terminal and type:
     **artsd -F 6 -S 256**
   (leave the terminal open)
2.edit the launcher et.sh (or whatever the name is...) and replace **./et.x86 "$@"** with:
    **artsdsp -m ./et.x86 "$@"**

Hope that helpes!

---

