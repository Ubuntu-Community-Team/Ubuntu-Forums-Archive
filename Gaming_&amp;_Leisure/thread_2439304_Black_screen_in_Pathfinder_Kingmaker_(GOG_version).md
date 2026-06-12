---
title: "Black screen in Pathfinder Kingmaker (GOG version)"
date: 2020-03-25
forum: Gaming &amp; Leisure
---

### Post by RedSword on 2020-03-25
Hi,

I recently installed Pathfinder Kingmaker with GOG installer (2.0.8). Game worked "fine" for the whole Chapter 1. I then got graphic artefact as soon as I reached Kingdom management world map. It seems very similar to what is describe with mesa for steam here : [https://gitlab.freedesktop.org/mesa/mesa/issues/952](https://gitlab.freedesktop.org/mesa/mesa/issues/952)  (there is an image in the middle of the comments).

I'm Ubuntu 18.04. I also played around with ingame configs : low/medium, fullscreen or not; nothing helps. See attachment for behaviour. 

[COLOR=#242729][FONT=Consolas]sudo lshw -c video ==> [/FONT][/COLOR] 
*-display 
    description: VGA compatible controller 
    product: Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X] 
    vendor: Advanced Micro Devices, Inc. [AMD/ATI] 
    physical id: 0 
    bus info: pci@0000:01:00.0 
    version: 00 
    width: 64 bits 
    clock: 33MHz 
    capabilities: pm pciexpress msi vga_controller bus_master cap_list rom         configuration: driver=radeon latency=0

Basically whenever I go to the Kingdom management world map and get out after having entered different zones, I get blackness for the main part of the screen. 

It can be starting (from launching the game; I mention this because loading a save, even from main menu doesn't have the same behaviour if you restart the game) : [from the world map, going to Tuskdale, then Throne Room, then Kingdom Affair map] OR [from the Throne Room, then main square Hub, then main square, then area exit --> All black] OR [from the Throne room --> Kingdom Affair map --> exit --> Main square Hub --> Main square --> All black]

I also seldom only have my character 3d model black, but not the rest black.

Any one had similar problem ? If so what was your fix ?

Thank you !

EDIT : I'll also post in the official forums shortly

---

### Post by mastablasta on 2020-03-26
ugh, that doesn't look good.
to start troubleshooting i suggest you launch the game from terminal and see if there is any errors being reported.

though form the link you posted it looks like game/drivers specific issue. and perhaps a bug of sorts.

---

### Post by RedSword on 2020-03-26
Yeah :/ . Logs (when going from the Throne Room, looking at Kingdom Affair map, exit, going to Main Square (=talking to the Nymph), going to world map, going back to Tusk Dale and going back to the Throne room) : 

```
Desktop is 1366 x 768 @ 60 HzNew context 0x2e53e30 created with attributes:
Initialize engine version: 2018.1.0f2 (d4d99f31acba)
GfxDevice: creating device client; threaded=1
Renderer: AMD TAHITI (DRM 2.50.0, 4.15.0-91-generic, LLVM 9.0.0)
Vendor:   X.Org
Version:  4.5 (Core Profile) Mesa 19.2.8
GLES:     0
 GL_AMD_conservative_depth GL_AMD_depth_clamp_separate GL_AMD_draw_buffers_blend GL_AMD_gpu_shader_int64 GL_AMD_multi_draw_indirect GL_AMD_performance_monitor GL_AMD_pinned_memory GL_AMD_query_buffer_object GL_AMD_seamless_cubemap_per_texture GL_AMD_shader_stencil_export GL_AMD_shader_trinary_minmax GL_AMD_texture_texture4 GL_AMD_vertex_shader_layer GL_AMD_vertex_shader_viewport_index GL_ANGLE_texture_compression_dxt3 GL_ANGLE_texture_compression_dxt5 GL_ARB_ES2_compatibility GL_ARB_ES3_1_compatibility GL_ARB_ES3_2_compatibility GL_ARB_ES3_compatibility GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_bindless_texture GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_color_buffer_float GL_ARB_compressed_texture_pixel_storage GL_ARB_compute_shader GL_ARB_compute_variable_group_size GL_ARB_conditional_render_inverted GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_bu
ffer_float GL_ARB_depth_clamp GL_ARB_derivative_control GL_ARB_direct_state_access GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_elements_base_vertex GL_ARB_draw_indirect GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_shader GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_gpu_shader_int64 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multi_draw_indirect GL_ARB_occlusion_query2 GL_ARB_parallel_shader_compile GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_sprite GL_ARB_polygon_offset_clamp GL_ARB_program_inter
face_query GL_ARB_provoking_vertex GL_ARB_query_buffer_object GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_seamless_cubemap_per_texture GL_ARB_separate_shader_objects GL_ARB_shader_atomic_counter_ops GL_ARB_shader_atomic_counters GL_ARB_shader_ballot GL_ARB_shader_bit_encoding GL_ARB_shader_clock GL_ARB_shader_group_vote GL_ARB_shader_image_load_store GL_ARB_shader_image_size GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_shader_stencil_export GL_ARB_shader_storage_buffer_object GL_ARB_shader_subroutine GL_ARB_shader_texture_image_samples GL_ARB_shader_texture_lod GL_ARB_shader_viewport_layer_array GL_ARB_shading_language_420pack GL_ARB_shading_language_packing GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_tessellation_shader GL_ARB_texture_barrier GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_buffer_range GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cu
be_map_array GL_ARB_texture_filter_anisotropic GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transform_feedback_instanced GL_ARB_transform_feedback_overflow_query GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_64bit GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ATI_blend_equation_separate GL_ATI_meminfo GL_ATI_texture_float GL_ATI_texture_mirror_once GL_EXT_abgr GL_EXT_blend_equation_separate GL_EXT_depth_bounds_test GL
_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_multisample_blit_scaled GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_memory_object GL_EXT_memory_object_fd GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_pixel_buffer_object GL_EXT_polygon_offset_clamp GL_EXT_provoking_vertex GL_EXT_shader_image_load_formatted GL_EXT_shader_integer_mix GL_EXT_texture_array GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_mirror_clamp GL_EXT_texture_sRGB GL_EXT_texture_sRGB_R8 GL_EXT_texture_sRGB_decode GL_EXT_texture_shared_exponent GL_EXT_texture_snorm GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_transform_feedback GL_EXT_vertex_array_bgra GL_EXT_vertex_attrib_64bit GL_EXT_window_rectangles GL_IBM_multimode_draw_arrays GL_KHR_blend_equation_advanced GL_KHR_context_flush_control GL_KHR_debug GL_KHR_no_error GL_KHR_paralle
l_shader_compile GL_KHR_robust_buffer_access_behavior GL_KHR_robustness GL_KHR_texture_compression_astc_ldr GL_KHR_texture_compression_astc_sliced_3d GL_MESA_pack_invert GL_MESA_shader_integer_functions GL_MESA_texture_signed_rgba GL_NVX_gpu_memory_info GL_NV_conditional_render GL_NV_depth_clamp GL_NV_packed_depth_stencil GL_NV_texture_barrier GL_NV_vdpau_interop GL_OES_EGL_image GL_S3_s3tc
OPENGL LOG: Creating OpenGL 4.5 graphics device ; Context level  <OpenGL 4.5> ; Context handle 48578096
Begin MonoManager ReloadAssembly
- Completed reload, in  0.816 seconds
WARNING: Shader Unsupported: 'PF/Clusters' - Pass 'INSTANCED GEOMETRY' has no vertex shader
New context 0x3efd720 created with attributes:
Default vsync count 0
requesting resize 1366 x 768
Using native desktop resolution 1366 x 768
requesting fullscreen 1366 x 768 at 0 Hz
Desktop is 1366 x 768 @ 60 Hz
UnloadTime: 1.079000 ms




[Manager] Injection...
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32.so
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/kernel32
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32.so
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32.so
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/kernel32
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32.so
Fallback handler could not load library /home/red/GOG Games/Pathfinder Kingmaker/game/Kingmaker_Data/Mono/libkernel32
[Manager] Initialize.
[Manager] Version: 0.21.5.0.
[Manager] OS: Unix 4.15.0.91 .
[Manager] Net Framework: 4.0.30319.42000.
[Manager] Unity Engine: 2018.1.2.
[Manager] Game: Pathfinder: Kingmaker.
[Manager] Mods path: /home/red/GOG Games/Pathfinder Kingmaker/Mods.
[Manager] Injection successful.
[Manager] Start parsing game version.
[Manager] Game version detected as '2.0.8'.
[Manager] Parsing mods.
[Manager] Reading file '/home/red/GOG Games/Pathfinder Kingmaker/Mods/CloserToTabletop/Info.json'.
[Manager] Reading file '/home/red/GOG Games/Pathfinder Kingmaker/Mods/TurnBased/Info.json'.
[Manager] Sorting mods.
[Manager] Loading mods.
[CloserToTabletop] Version '1.2.3'. Loading.
[CloserToTabletop] Active.
[CloserToTabletop] Loading time 0.46 s.
[TurnBased] Version '1.0.9'. Loading.
[TurnBased] Active.
[TurnBased] Loading time 3.89 s.
[Manager] FINISH. SUCCESSFUL LOADED 2/2 MODS.




[Manager] Checking for updates.
Setting up 3 worker threads for Enlighten.
  Thread -> id: 7f1e911ec700 -> priority: 1 
  Thread -> id: 7f1e7bfff700 -> priority: 1 
  Thread -> id: 7f1e7b7fe700 -> priority: 1 
The loaded level has a different lightmaps mode than the current one. Current: Directional. Loaded: Non-Directional. Will use: Directional.
 
(Filename:  Line: 510)


Show
The AssetBundle 'shaders' can't be loaded because another AssetBundle with the same files is already loaded.
 
(Filename:  Line: 438)


The AssetBundle 'common_assets' can't be loaded because another AssetBundle with the same files is already loaded.
 
(Filename:  Line: 438)


Set Areas Folder to /home/red/.config/unity3d/Owlcat Games/Pathfinder Kingmaker/Areas
Unloading 11 Unused Serialized files (Serialized files now loaded: 14)


Unloading 1697 unused Assets to reduce memory usage. Loaded Objects now: 502206.
Total: 1468.604000 ms (FindLiveObjects: 66.322000 ms CreateObjectMapping: 61.617000 ms MarkObjects: 1336.528000 ms  DeleteObjects: 4.136000 ms)


Await event system
Await input module
The referenced script on this Behaviour (Game Object 'ClothCollider (1) pelvis') is missing!
 
(Filename:  Line: 1789)


The loaded level has a different lightmaps mode than the current one. Current: Directional. Loaded: Non-Directional. Will use: Directional.
 
(Filename:  Line: 510)


Await event system
Await input module
NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Visual.WindController.Update () [0x00005] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


Unloading 24 Unused Serialized files (Serialized files now loaded: 344)


Unloading 6206 unused Assets to reduce memory usage. Loaded Objects now: 637600.
Total: 1593.972000 ms (FindLiveObjects: 94.095000 ms CreateObjectMapping: 87.427000 ms MarkObjects: 1330.021000 ms  DeleteObjects: 82.429000 ms)


Await event system
Await input module
FogOfWarStaticMaskHolder bounds is not completely placed inside in LocationMaskRenderer bounds [CapitalSquareVillage_Static]
 
(Filename: /home/builduser/buildslave/unity/build/Runtime/Export/Debug.bindings.h Line: 43)


FogOfWarStaticMaskHolder bounds is not completely placed inside in LocationMaskRenderer bounds [CapitalSquareVillage_Static]
 
(Filename: /home/builduser/buildslave/unity/build/Runtime/Export/Debug.bindings.h Line: 43)


Precision issue while prewarming particle system - 'Duration' or 'Start Lifetime' is likely a too large value.
 
(Filename:  Line: 1317)


Precision issue while prewarming particle system - 'Duration' or 'Start Lifetime' is likely a too large value.
 
(Filename:  Line: 1317)


Precision issue while prewarming particle system - 'Duration' or 'Start Lifetime' is likely a too large value.
 
(Filename:  Line: 1317)


Precision issue while prewarming particle system - 'Duration' or 'Start Lifetime' is likely a too large value.
 
(Filename:  Line: 1317)


The loaded level has a different lightmaps mode than the current one. Current: Directional. Loaded: Non-Directional. Will use: Directional.
 
(Filename:  Line: 510)


Coroutine couldn't be started because the the game object 'tavern_paper_2 (13)' is inactive!
 
(Filename:  Line: 784)


Coroutine couldn't be started because the the game object 'tavern_paper_2 (14)' is inactive!
 
(Filename:  Line: 784)


Coroutine couldn't be started because the the game object 'tavern_paper_1 (9)' is inactive!
 
(Filename:  Line: 784)


Material doesn't have a texture property '_MainTex'
 
(Filename:  Line: 1220)


Material doesn't have a texture property '_MainTex'
 
(Filename:  Line: 1220)


Material doesn't have a texture property '_MainTex'
 
(Filename:  Line: 1220)


Coroutine couldn't be started because the the game object 'tavern_paper_2 (11)' is inactive!
 
(Filename:  Line: 784)


Coroutine couldn't be started because the the game object 'tavern_paper_1 (8)' is inactive!
 
(Filename:  Line: 784)


Coroutine couldn't be started because the the game object 'tavern_paper_2 (10)' is inactive!
 
(Filename:  Line: 784)


Coroutine couldn't be started because the the game object 'tavern_paper_2 (9)' is inactive!
 
(Filename:  Line: 784)


Unloading 59 Unused Serialized files (Serialized files now loaded: 256)


Unloading 5043 unused Assets to reduce memory usage. Loaded Objects now: 657038.
Total: 1757.142000 ms (FindLiveObjects: 97.027000 ms CreateObjectMapping: 90.750000 ms MarkObjects: 1492.112000 ms  DeleteObjects: 77.252000 ms)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Globalmap.GlobalMapLandmark.OnEnable () [0x00000] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Globalmap.GlobalMapLandmark.OnEnable () [0x00000] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Globalmap.GlobalMapLandmark.OnEnable () [0x00000] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Globalmap.GlobalMapLandmark.OnEnable () [0x00000] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Globalmap.GlobalMapLandmark.OnEnable () [0x00000] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Globalmap.GlobalMapLandmark.OnEnable () [0x00000] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Globalmap.GlobalMapLandmark.OnEnable () [0x00000] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


NullReferenceException: Object reference not set to an instance of an object
  at Kingmaker.Globalmap.GlobalMapLandmark.OnEnable () [0x00000] in <73701c29fe67487b9b233be164aa8cd1>:0 
 
(Filename: <73701c29fe67487b9b233be164aa8cd1> Line: 0)


Unloading 12 Unused Serialized files (Serialized files now loaded: 140)


Unloading 2506 unused Assets to reduce memory usage. Loaded Objects now: 541994.
Total: 1616.401000 ms (FindLiveObjects: 79.003000 ms CreateObjectMapping: 70.188000 ms MarkObjects: 1440.951000 ms  DeleteObjects: 26.257000 ms)


Await event system
Await input module
The referenced script on this Behaviour (Game Object 'ClothCollider (1) pelvis') is missing!
 
(Filename:  Line: 1789)


The AssetBundle 'capitalthroneroom_light_bundle' can't be loaded because another AssetBundle with the same files is already loaded.
 
(Filename:  Line: 438)

```

[FONT=Helvetica]Note the interesting :[/FONT]
[FONT=Helvetica]&#8220;The AssetBundle &#8216;capitalthroneroom_light_bundle&#8217; can&#8217;t be loaded because another AssetBundle with the same files is already loaded.&#8221;[/FONT]
[FONT=Helvetica]as well as[/FONT]
[FONT=Helvetica]&#8220;Material doesn&#8217;t have a texture property &#8216;_MainTex&#8217;&#8221;[/FONT]
[FONT=Helvetica](and a lot of NullReferenceException)[/FONT]

---

### Post by RedSword on 2020-03-26
Partly solved by scaling down the resolution in-game. Now less important parts are all-black and the game is more playable.

EDIT : Turns out I had to update my mesa drivers.

---

