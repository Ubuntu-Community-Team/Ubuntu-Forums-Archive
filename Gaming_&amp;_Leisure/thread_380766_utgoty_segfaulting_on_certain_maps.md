---
title: "ut:goty segfaulting on certain maps"
date: 2007-03-10
forum: Gaming &amp; Leisure
---

### Post by aidanr on 2007-03-10
like the title says, the following maps segfault on me
```
galleon
grinder
gearbolt
condemned
the gauntlet
eternal cave
november
overlord
```
```
command:ut
command:Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
Game class is 'UTIntro'
Level is Level Entry.MyLevel
Bringing Level Entry.MyLevel up for play (0)...
InitGame: 
Base Mutator is Entry.Mutator0
Browse: CityIntro.unr?Name=aidanr?Class=Botpack.TMale1?team=255?skin=CommandoSkins.cmdo?Face=CommandoSkins.Whitman?Voice=BotPack.VoiceMaleOne
LoadMap: CityIntro.unr?Name=aidanr?Class=Botpack.TMale1?team=255?skin=CommandoSkins.cmdo?Face=CommandoSkins.Whitman?Voice=BotPack.VoiceMaleOne
Case-insensitive search: genfluid -> ..\Textures\GenFluid.utx
Collecting garbage
Purging garbage
-0.0ms Unloading: Package Render
Garbage: objects: 16417->16416; refs: 224678
Game class is 'UTIntro'
Level is Level CityIntro.MyLevel
Bringing Level CityIntro.MyLevel up for play (0)...
InitGame: ?Name=aidanr?Class=Botpack.TMale1?team=255?skin=CommandoSkins.cmdo?Face=CommandoSkins.Whitman?Voice=BotPack.VoiceMaleOne
Base Mutator is CityIntro.Mutator1
Initialized moving brush tracker for Level CityIntro.MyLevel
Created and initialized a new SDL viewport.
Bound to UWeb.so
Team 255
Login: aidanr
Possessed PlayerPawn: TMale1 CityIntro.TMale0
Input system initialized for SDLViewport0
Opening SDL viewport.
Bound to OpenGLDrv.so
Loaded render device class.
Initializing OpenGLDrv...
binding libGL.so.1
Resizing SDL viewport. X: 1440 Y: 900
OpenGL
GL_VENDOR     : NVIDIA Corporation
GL_RENDERER   : GeForce 6800/PCI/SSE2
GL_VERSION    : 2.1.0 NVIDIA 97.55
GL_EXTENSIONS : GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
Device supports: GL_EXT_bgra
Device supports: GL_ARB_texture_compression
Device supports: GL_EXT_texture_compression_s3tc
Device supports: GL_EXT_texture_env_combine
Device supports: GL_ARB_texture_env_combine
Device supports: GL_EXT_texture_filter_anisotropic
Device supports: GL_NV_texture_env_combine4
Device supports: GL_EXT_texture_lod_bias
Device supports: GL_EXT_compiled_vertex_array
Device supports: GL_EXT_secondary_color
Device supports: GL_ARB_multitexture
Device supports: GL_SGIS_generate_mipmap
Device supports: GL_NV_multisample_filter_hint
Device supports: GL_EXT_multi_draw_arrays
Device supports: GL_ARB_vertex_program
Depth bits: 16
4 Texture Mapping Units found
MaxAnisotropy = 16
Trying to use S3TC extension.
MinLogTextureSize = 2
MaxLogTextureSize = 12
Bound to ALAudio.so
fcntl: Operation not permitted
fcntl: Operation not permitted
OpenAL Audio subsystem initialized.
Game engine initialized
Startup time: 2.281045 seconds.
Entering main loop.
URL: Adding default option Name=aidanr
URL: Adding default option Class=Botpack.TMale1
URL: Adding default option team=255
URL: Adding default option skin=CommandoSkins.cmdo
URL: Adding default option Face=CommandoSkins.Whitman
URL: Adding default option Voice=BotPack.VoiceMaleOne
Browse: Index.unr?entry?Name=aidanr?Class=Botpack.TMale1?team=255?skin=CommandoSkins.cmdo?Face=CommandoSkins.Whitman?Voice=BotPack.VoiceMaleOne
Failed; returning to Entry
Shut down moving brush tracker for Level CityIntro.MyLevel
Spawning new actor for Viewport SDLViewport0
Team 255
Login: aidanr
Possessed PlayerPawn: TMale1 Entry.TMale1
Creating root window: UMenu.UMenuRootWindow
Export travel for: aidanr
Exporting travelling actor of class Botpack.TMale1
URL: Adding default option Name=aidanr
URL: Adding default option Class=Botpack.TMale1
URL: Adding default option team=255
URL: Adding default option skin=CommandoSkins.cmdo
URL: Adding default option Face=CommandoSkins.Whitman
URL: Adding default option Voice=BotPack.VoiceMaleOne
Browse: UT-Logo-Map.unr?Game=Botpack.LadderLoadGame?Name=aidanr?Class=Botpack.TMale1?team=255?skin=CommandoSkins.cmdo?Face=CommandoSkins.Whitman?Voice=BotPack.VoiceMaleOne
LoadMap: UT-Logo-Map.unr?Game=Botpack.LadderLoadGame?Name=aidanr?Class=Botpack.TMale1?team=255?skin=CommandoSkins.cmdo?Face=CommandoSkins.Whitman?Voice=BotPack.VoiceMaleOne
Collecting garbage
Purging garbage
-0.0ms Unloading: Package CityIntro
-0.0ms Unloading: Package city
-0.0ms Unloading: Package Detail
-0.0ms Unloading: Package ArenaTex
-0.0ms Unloading: Package GenFX
-0.0ms Unloading: Package NaliCast
-0.0ms Unloading: Package RainFX
-0.0ms Unloading: Package DecayedS
-0.0ms Unloading: Package GenIn
-0.0ms Unloading: Package NaliFX
-0.0ms Unloading: Package genfluid
-0.0ms Unloading: Package ShaneSky
-0.0ms Unloading: Package AmbModern
-0.0ms Unloading: Package AmbAncient
-0.0ms Unloading: Package AmbOutside
-0.0ms Unloading: Package Uttitle
-0.0ms Unloading: Package openingwave
-0.0ms Unloading: Package MultiMesh
-0.0ms Unloading: Package EpicCustomModels
Garbage: objects: 22330->20768; refs: 236484
Game class is 'LadderLoadGame'
Level is Level UT-Logo-Map.MyLevel
Bringing Level UT-Logo-Map.MyLevel up for play (0)...
InitGame: ?Game=Botpack.LadderLoadGame?Name=aidanr?Class=Botpack.TMale1?team=255?skin=CommandoSkins.cmdo?Face=CommandoSkins.Whitman?Voice=BotPack.VoiceMaleOne
Base Mutator is UT-Logo-Map.Mutator2
Spawning new actor for Viewport SDLViewport0
Team 255
Login: aidanr
Possessed PlayerPawn: TMale1 UT-Logo-Map.TMale2
Incoming travelling actor of class Botpack.TMale1
Initialized moving brush tracker for Level UT-Logo-Map.MyLevel
UT-Logo-Map.LadderInventory0 giveto UT-Logo-Map.TMale2
Current Ladder is Botpack.LadderDM
Case-insensitive search: genfluid -> ..\Textures\GenFluid.utx
Case-insensitive search: DM-Kgalleon -> ..\Maps\DM-KGalleon.unr
Signal: SIGSEGV [segmentation fault]
Aborting.
Exiting.
Name subsystem shut down
Allocation checking disabled
Segmentation fault (core dumped)

```

any ideas? :confused:

---

### Post by aidanr on 2007-03-10
i just compared md5sums of KGalleon and GenFluid, KGalleon is fine, but GenFluid is different, so i'm assuming i have some corrupt files in the installation :( 

oh well, at least i know how to fix it now :smile:

---

### Post by AJB2K3 on 2007-03-10
I couldn't get the mas converted in nix so had to rip mine from the xp install.
Try installing under wine then copying the files over.

---

### Post by aidanr on 2007-03-10
good idea, i'll try that later

---

### Post by AJB2K3 on 2007-03-10
> **aidanr said:**
> good idea, i'll try that later
Im getting it trying to run ucc make.

---

### Post by aidanr on 2007-03-10
ok so i tried that and it worked great

for reference, i installed via wine
then ran the linux installer, telling it to only install the binaries, and then copied everything from the wine install folder to the linux install folder while _not_ overwriting any files

---

### Post by AJB2K3 on 2007-03-11
> **aidanr said:**
> ok so i tried that and it worked great


Glad it worked for you.
I have it installed on xp (to get all the addons) and just copyed all the files from that install to cd then copyed from the cd to Ubuntu.
Just need to work on Chaos UT.

---

