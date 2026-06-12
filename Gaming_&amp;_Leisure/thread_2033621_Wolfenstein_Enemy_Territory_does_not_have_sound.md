---
title: "Wolfenstein: Enemy Territory does not have sound"
date: 2012-07-26
forum: Gaming &amp; Leisure
---

### Post by Subcomfreak on 2012-07-26
Seems to be a pretty common problem, but all of the common fixes don't work for me :P

There is obviously no sound while playing the game**. **I have a different error than what everyone else seems to be getting on start up of the game:```
et
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/john/.etwolf/etmain/supply_pro.pk3 (66 files)
/home/john/.etwolf/etmain/1944_beach.pk3 (60 files)
/home/john/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3889 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/CooLDoG/etconfig.cfg
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
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI R200 (RV280 5961) x86/MMX/SSE TCL DRI2
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc.
GL_RENDERER: Mesa DRI R200 (RV280 5961) x86/MMX/SSE TCL DRI2
GL_VERSION: 1.3 Mesa 8.0.2
GL_EXTENSIONS: GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_ARB_occlusion_query GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_fragment_shader GL_EXT_texture_cube_map GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_vertex_program GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_texture_rectangle GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_packed_depth_stencil GL_ARB_vertex_array_object GL_ATI_texture_mirror_once GL_EXT_gpu_program_parameters GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_robustness 
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_MESA_multithread_makecurrent GLX_MESA_swap_control GLX_OML_swap_method GLX_OML_sync_control GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGI_video_sync GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGIX_visual_select_group GLX_EXT_texture_from_pixmap 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 6

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
[U][B]/dev/dsp: No such file or directory
Could not open /dev/dsp[/B][/U]
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/john/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/john/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/john/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0x97caf40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: 11ukkhunbuntu
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: Attempting to resolve master3.evenbalance.com
^5PunkBuster Client: Resolved to [216.240.146.139] (0)
^5PunkBuster Client: PunkBuster Client (v2.254 | A0) Enabled
^5PunkBuster Client: Game Version [ET 2.60b linux-i386 May  8 2006]
^5PunkBuster Client: Not Connected to a Server
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
john@11ukkhunbuntu:~$ 

```
See bolded line.

Thanks in advance for your help!

---

### Post by garyzw on 2012-07-27
I use this script: [wolfsp-sdl-sound.sh]("http://bloc.eurion.net/wp-content/uploads/2009/12/wolfsp-sdl-sound.sh")

a) Download this script: [wolfsp-sdl-sound.sh]("http://bloc.eurion.net/wp-content/uploads/2009/12/wolfsp-sdl-sound.sh") ([original download link]("http://nullkey.ath.cx/%7Estuff/et-sdl-sound/wolfsp-sdl-sound.gz"), [alternative download link]("http://members.lycos.co.uk/lordbanter/wolfsp-sdl-sound.gz")), created by [Pyry Haulos]("http://nullkey.ath.cx/").
 

b) Open it with a text editor and customize it to match your configuration: change the line «*GAME_PATH=”/home/games/enemy-territory”*» to point to the location of your *Enemy Territory* installation (most likely «*GAME_PATH=”/usr/local/games/enemy-territor”*»); in case your directory with the game files isn’t called «*enemy-territory*» like in the example you’ll also need to adapt the *GAME_DIR* variable.
 

c) Save this file somewhere on your computer, make it executable if  needed (you can do this by right clicking on it, selecting “Properties”  and under the “Permissions” tab of the dialogue that will show up  checking the box to allow execution of the file). Done, now whenever you  want to run the game just start it by running this file.

---

### Post by Subcomfreak on 2012-07-27
Seems to be working! Many thanks. Support for ubuntu is way better than Windows!!!

---

### Post by garyzw on 2012-07-27
> **Subcomfreak said:**
> Seems to be working! Many thanks. Support for ubuntu is way better than Windows!!!

You are welcome.  Glad to help.

Mark the thread as solved! :)

---

