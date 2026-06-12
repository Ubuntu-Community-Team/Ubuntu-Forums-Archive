---
title: "sound issues with darkplaces"
date: 2009-12-25
forum: Gaming &amp; Leisure
---

### Post by commodore256 on 2009-12-25
As you can tell by the title, I'm sound problems with the darkplaces engine.

I'm trying to run the shareware version of quake1 inside of darkplaces, but Sound only works for one second and then mutes.

Here's my console:

```
./darkplaces-linux-686-glx -basedir ~/Desktop/quake106/
DarkPlaces-Quake Linux 19:55:23 Jul  9 2009 - release
Trying to load library... "libz.so.1" - loaded.
Added packfile /home/cj/Desktop/quake106/id1/pak0.pak (339 files)
Playing shareware version.
Trying to load library... "libcurl.so.4" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libogg.so.0" - loaded.
Trying to load library... "libtheora.so.0" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisenc.so.2" - loaded.
Trying to load library... "libOffscreenGecko.so" "./libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing config.cfg
couldn't exec autoexec.cfg
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Client opened a socket on address [0:0:0:0:0:0:0:0]:0
Playing demo demo1.dem.
Initializing Video Mode: fullscreen 1024x768x32x60hz
Loading OpenGL driver libGL.so.1
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 915G GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.6
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
S_Startup: initializing sound output format: 44000Hz, 16 bit, 2 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
Sound format: 44000Hz, 2 channels, 16 bits per sample
ioctl CDROMREADTOCHDR failed
CDAudio_Init: No CD in player.
Initial CD volume: 1
CD Audio Initialized


<===================================>

the Necropolis
ioctl CDROMREADTOCHDR failed
No CD in player.
You got the shells
You got the Grenade Launcher

```

I've also tried the default 48k. I only get the sound back when I change my resolution and then it only works for one second and then mutes again. I've also checked the sound settings in options.

I get more sound by running this in dosbox, but I don't wanna do that. I wanna run it natively in the best detail as possible.

---

### Post by Sindwiller on 2009-12-26
Huh, weird... offscreengecko is the only library not successfully loaded, but it doesn't have anything to do with your sound problem. The DP readme doesn't mention anything about sound parameters/known sound issues either.

Did you try to run Darkplaces with the -developer parameter on?

---

### Post by commodore256 on 2009-12-27
OK, here's my new console output.

```
./darkplaces-linux-686-glx -basedr ~/Desktop/quake106/ -developer
Console initialized.
DarkPlaces-Quake Linux 19:55:23 Jul  9 2009 - release
Trying to load library... "libz.so.1" - loaded.
Added packfile /home/cj/Desktop/quake106/id1/pak0.pak (339 files)
Playing shareware version.
Trying to load library... "libcurl.so.4" - loaded.
Initializing client
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libogg.so.0" - loaded.
Trying to load library... "libtheora.so.0" - loaded.
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisenc.so.2" - loaded.
Trying to load library... "libOffscreenGecko.so" "./libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing config.cfg
couldn't exec autoexec.cfg
3 demo(s) in loop
CL_Disconnect
Host_ShutdownServer
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:0
Client opened a socket on address [0:0:0:0:0:0:0:0]:0
Playing demo demo1.dem.
Initializing Video Mode: fullscreen 1024x768x32x60hz
Loading OpenGL driver libGL.so.1
Using XFree86-VidModeExtension Version 2.2
Using XVidMode fullscreen mode at 1024x768
checking for GLX_ARB_get_proc_address...  enabled
checking for GLX_SGI_swap_control...  not detected
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 915G GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.6
GL_EXTENSIONS: GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_MESA_swap_frame_usage GLX_OML_swap_method GLX_SGI_video_sync GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group GLX_EXT_texture_from_pixmap 
checking for OpenGL 1.1 core features...  enabled
Checking OpenGL extensions...
checking for OpenGL 1.2 core features...  enabled
checking for GL_ARB_multitexture...  enabled
checking for GL_ARB_texture_env_combine...  enabled
checking for GL_ARB_texture_env_dot3...  enabled
checking for GL_EXT_texture3D...  enabled
checking for GL_ARB_texture_cube_map...  enabled
checking for GL_ARB_texture_compression...  enabled
checking for GL_EXT_compiled_vertex_array...  enabled
checking for GL_EXT_texture_edge_clamp...  enabled
checking for GL_EXT_texture_filter_anisotropic...  enabled
checking for GL_EXT_blend_minmax...  enabled
checking for GL_EXT_blend_subtract...  enabled
checking for OpenGL 2.0 core features...  not detected (OpenGL 1.4 loaded)
checking for GL_ATI_separate_stencil...  enabled
checking for GL_EXT_stencil_two_side...  enabled
checking for GL_ARB_vertex_buffer_object...  enabled
checking for GL_ARB_shader_objects...  not detected
checking for GL_ARB_occlusion_query...  not detected

QuakeC extensions for server and client: BX_WAL_SUPPORT DP_BUTTONCHAT DP_BUTTONUSE DP_CL_LOADSKY DP_CON_ALIASPARAMETERS DP_CON_BESTWEAPON DP_CON_EXPANDCVAR DP_CON_SET DP_CON_SETA DP_CON_STARTMAP DP_CSQC_MULTIFRAME_INTERPOLATION DP_EF_ADDITIVE DP_EF_BLUE DP_EF_DOUBLESIDED DP_EF_FLAME DP_EF_FULLBRIGHT DP_EF_NODEPTHTEST DP_EF_NODRAW DP_EF_NOGUNBOB DP_EF_NOSELFSHADOW DP_EF_NOSHADOW DP_EF_RED DP_EF_STARDUST DP_EF_TELEPORT_BIT DP_ENT_ALPHA DP_ENT_COLORMOD DP_ENT_CUSTOMCOLORMAP DP_ENT_EXTERIORMODELTOCLIENT DP_ENT_GLOW DP_ENT_LOWPRECISION DP_ENT_SCALE DP_ENT_VIEWMODEL DP_GECKO_SUPPORT DP_GFX_EXTERNALTEXTURES DP_GFX_EXTERNALTEXTURES_PERMAP DP_GFX_FOG DP_GFX_QUAKE3MODELTAGS DP_GFX_SKINFILES DP_GFX_SKYBOX DP_GFX_MODEL_INTERPOLATION DP_HALFLIFE_MAP DP_HALFLIFE_MAP_CVAR DP_HALFLIFE_SPRITE DP_INPUTBUTTONS DP_LITSPRITES DP_LITSUPPORT DP_MONSTERWALK DP_MOVETYPEBOUNCEMISSILE DP_MOVETYPEFOLLOW DP_NULL_MODEL DP_QC_ASINACOSATANATAN2TAN DP_QC_CHANGEPITCH DP_QC_CMD DP_QC_COPYENTITY DP_QC_CRC16 DP_QC_CVAR_DEFSTRING DP_QC_CVAR_DESCRIPTION DP_QC_CVAR_STRING DP_QC_CVAR_TYPE DP_QC_EDICT_NUM DP_QC_ENTITYDATA DP_QC_ETOS DP_QC_EXTRESPONSEPACKET DP_QC_FINDCHAIN DP_QC_FINDCHAIN_TOFIELD DP_QC_FINDCHAINFLAGS DP_QC_FINDCHAINFLOAT DP_QC_FINDFLAGS DP_QC_FINDFLOAT DP_QC_FS_SEARCH DP_QC_GETLIGHT DP_QC_GETSURFACE DP_QC_GETSURFACEPOINTATTRIBUTE DP_QC_GETTAGINFO DP_QC_GETTAGINFO_BONEPROPERTIES DP_QC_GETTIME DP_QC_GETTIME_CDTRACK DP_QC_MINMAXBOUND DP_QC_MULTIPLETEMPSTRINGS DP_QC_NUM_FOR_EDICT DP_QC_RANDOMVEC DP_QC_SINCOSSQRTPOW DP_QC_STRFTIME DP_QC_STRINGBUFFERS DP_QC_STRINGBUFFERS_CVARLIST DP_QC_STRINGCOLORFUNCTIONS DP_QC_STRING_CASE_FUNCTIONS DP_QC_STRREPLACE DP_QC_TOKENIZEBYSEPARATOR DP_QC_TOKENIZE_CONSOLE DP_QC_TRACEBOX DP_QC_TRACETOSS DP_QC_TRACE_MOVETYPE_HITMODEL DP_QC_TRACE_MOVETYPE_WORLDONLY DP_QC_UNLIMITEDTEMPSTRINGS DP_QC_URI_ESCAPE DP_QC_URI_GET DP_QC_VECTOANGLES_WITH_ROLL DP_QC_VECTORVECTORS DP_QC_WHICHPACK DP_QUAKE2_MODEL DP_QUAKE2_SPRITE DP_QUAKE3_MAP DP_QUAKE3_MODEL DP_REGISTERCVAR DP_SND_DIRECTIONLESSATTNNONE DP_SND_FAKETRACKS DP_SND_OGGVORBIS DP_SND_STEREOWAV DP_SOLIDCORPSE DP_SPRITE32 DP_SV_BOTCLIENT DP_SV_BOUNCEFACTOR DP_SV_CLIENTCOLORS DP_SV_CLIENTNAME DP_SV_CMD DP_SV_CUSTOMIZEENTITYFORCLIENT DP_SV_DRAWONLYTOCLIENT DP_SV_DROPCLIENT DP_SV_EFFECT DP_SV_ENTITYCONTENTSTRANSITION DP_SV_MODELFLAGS_AS_EFFECTS DP_SV_MOVETYPESTEP_LANDEVENT DP_SV_NETADDRESS DP_SV_NODRAWTOCLIENT DP_SV_ONENTITYNOSPAWNFUNCTION DP_SV_ONENTITYPREPOSTSPAWNFUNCTION DP_SV_PING DP_SV_PLAYERPHYSICS DP_SV_POINTPARTICLES DP_SV_POINTSOUND DP_SV_PRECACHEANYTIME DP_SV_PRINT DP_SV_PUNCHVECTOR DP_SV_QCSTATUS DP_SV_ROTATINGBMODEL DP_SV_SETCOLOR DP_SV_SHUTDOWN DP_SV_SLOWMO DP_SV_SPAWNFUNC_PREFIX DP_SV_WRITEPICTURE DP_SV_WRITEUNTERMINATEDSTRING DP_TE_BLOOD DP_TE_BLOODSHOWER DP_TE_CUSTOMFLASH DP_TE_EXPLOSIONRGB DP_TE_FLAMEJET DP_TE_PARTICLECUBE DP_TE_PARTICLERAIN DP_TE_PARTICLESNOW DP_TE_PLASMABURN DP_TE_QUADEFFECTS1 DP_TE_SMALLFLASH DP_TE_SPARK DP_TE_STANDARDEFFECTBUILTINS DP_TRACE_HITCONTENTSMASK_SURFACEINFO DP_VIEWZOOM EXT_BITSHIFT FRIK_FILE FTE_QC_CHECKPVS FTE_STRINGS KRIMZON_SV_PARSECLIENTCOMMAND NEH_CMD_PLAY2 NEH_RESTOREGAME NEXUIZ_PLAYERMODEL NXQ_GFX_LETTERBOX PRYDON_CLIENTCURSOR TENEBRAE_GFX_DLIGHTS TW_SV_STEPCONTROL ZQ_PAUSE 
QuakeC extensions for menu: BX_WAL_SUPPORT DP_CINEMATIC_DPV DP_FONT_VARIABLEWIDTH DP_GECKO_SUPPORT DP_MENU_EXTRESPONSEPACKET DP_QC_ASINACOSATANATAN2TAN DP_QC_CMD DP_QC_CRC16 DP_QC_CVAR_TYPE DP_QC_CVAR_DESCRIPTION DP_QC_FINDCHAIN_TOFIELD DP_QC_RENDER_SCENE DP_QC_STRFTIME DP_QC_STRINGBUFFERS DP_QC_STRINGBUFFERS_CVARLIST DP_QC_STRINGCOLORFUNCTIONS DP_QC_STRING_CASE_FUNCTIONS DP_QC_STRREPLACE DP_QC_TOKENIZEBYSEPARATOR DP_QC_TOKENIZE_CONSOLE DP_QC_UNLIMITEDTEMPSTRINGS DP_QC_URI_ESCAPE DP_QC_URI_GET DP_QC_WHICHPACK FTE_STRINGS 
GL_MAX_ELEMENTS_VERTICES = 3000
GL_MAX_ELEMENTS_INDICES = 3000
GL_MAX_TEXTUREUNITS = 8
OpenGL backend started.
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
S_Startup: initializing sound output format: 44000Hz, 16 bit, 2 channels...
SndSys_Init: using the ALSA module
SndSys_Init: PCM device is "default"
Sound format: 44000Hz, 2 channels, 16 bits per sample
ioctl CDROMREADTOCHDR failed
CDAudio_Init: No CD in player.
Initial CD volume: 1
CD Audio Initialized
========Initialized=========
Serverinfo packet received.
Server protocol is QUAKEDP


<===================================>

the Necropolis
Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)ioctl CDROMREADTOCHDR failed
No CD in player.
Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)Mem_Free: data == NULL (called at model_shared.c:429)You got the shells
You got the Grenade Launcher
CL_Disconnect
Host_ShutdownServer
Require all of: 
OpenGL Backend shutting down

```

I don't know what all of it means.

---

### Post by Sindwiller on 2009-12-27
Weird, DP doesn't report any problems with your sound card or your ALSA or anything. Neither does it report that any of your sound files are b0rked. You don't have any sound problems with other applications, do you? It might be an ALSA- or config-related issue.

You could also ask over at #darkplaces @ irc.anynet.org, if the channel is still alive, that is.

---

### Post by commodore256 on 2009-12-27
I have other problems with sound too.

Tweetdeck sometimes displays the notification without a chirp. (I thought that was adobe's fault)

I can't hear the music on fretsonfire. (I just noticed that one today)

But, the video players are fine.

---

### Post by Sindwiller on 2009-12-28
Did you check the permissions for your audio devicefiles, as described on [on this page]("https://wiki.ubuntu.com/DebuggingSoundProblems#Checking%20permissions%20and%20resources")? There's some other useful stuff on that page that might help you.

Did you consider asking in the Darkplaces IRC channel, as I posted above?

---

### Post by commodore256 on 2010-01-01
It was a combination of running it in sdl and messing with user groups.

---

### Post by Huufarted on 2010-02-04
Could you elaborate, good sir?  I'm having the same issue.

---

### Post by andlinux on 2010-04-10
> **Huufarted said:**
> Could you elaborate, good sir?  I'm having the same issue.

Me too :(

---

### Post by sodar on 2011-03-04
just add:

```
_snd_mixahead 0.9
```to autoexec.cfg in your quake directory

---

