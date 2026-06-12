---
title: "StepMania"
date: 2008-01-10
forum: Gaming &amp; Leisure
---

### Post by starcraft708 on 2008-01-10
Every time I open StepMania the screen turns out black. This is from the log.txt: if anyone can help

00:00.043: StepMania 3.9

00:00.043: Log starting 2008-01-11 01:05:22

00:00.043:  

00:00.044: Reading 'Data/Defaults.ini' failed: No such file or directory

00:00.045: Reading 'Data/Static.ini' failed: No such file or directory

00:00.130: Loading window: gtk

00:00.130: OS: Linux ver 020622

00:00.130: Crash backtrace component: x86 custom backtrace

00:00.130: Crash lookup component: dladdr

00:00.130: Crash demangle component: cxa_demangle

00:00.130: Runtime library: glibc 2.6.1

00:00.130: Threads library: NPTL 2.6.1

00:00.130: TLS is available

00:00.130: AnnouncerManager::AnnouncerManager()

00:00.131: Reading 'Data/Static.ini' failed: No such file or directory

00:00.131: ThemeManager::SwitchThemeAndLanguage: "default", ""

00:00.172: Initializing driver: ALSA

00:00.236: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).

00:00.236: ALSA Driver: 0: NVidia nForce2 [nForce2], device 0: Intel ICH [NVidia nForce2], 1/1 subdevices avail

00:00.236: ALSA Driver: 0: NVidia nForce2 [nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958], 1/1 subdevices avail

00:00.236: ALSA Driver: 2: Logitech USB Headset [Headset], device 0: USB Audio [USB Audio], 1/1 subdevices avail

00:00.238: ALSA error: pcm_hw.c:1242 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy)

00:00.239: Could only create 1 buffers; need at least 8 (failed with dsnd_pcm_open(hw:0): Device or resource busy).  Hardware ALSA driver can't be used.

00:00.239: Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing

00:00.239: Initializing driver: ALSA-sw

00:00.239: OS: Linux ver 020622

00:00.240: ALSA: Software mixing at 44100hz

00:00.240: Starting thread: Decode thread

00:00.241: Starting thread: RageSound_ALSA9_Software

00:00.241: Sound driver: ALSA-sw

00:00.241: Starting thread: MusicThread

00:00.246: Initializing lights driver: Null

00:00.253: Reading 'Cache/index.cache' failed: No such file or directory

00:00.253: Cache format is out of date.  Deleting all cache files.

00:00.253: remove '/home/thomas/Documents/StepMania-3.9/Cache/banners.cache'

00:00.253: remove '/home/thomas/Documents/StepMania-3.9/Cache/Banners/1527817133'

00:00.253: remove '/home/thomas/Documents/StepMania-3.9/Cache/Banners/1654699250'

00:00.253: remove '/home/thomas/Documents/StepMania-3.9/Cache/Banners/543857581'

00:00.254: remove '/home/thomas/Documents/StepMania-3.9/Cache/Banners/585729452'

00:00.254: Reading 'Cache/banners.cache' failed: No such file or directory

00:00.257: Found 0 songs in 0.000144 seconds.

00:00.257: Loading courses.

00:00.406: Course::LoadFromCRSFile( 'Courses/Samples/AllChallenge.crs' )

00:00.413: Course::LoadFromCRSFile( 'Courses/Samples/AllMusicRandom.crs' )

00:00.414: Course::LoadFromCRSFile( 'Courses/Samples/EndOfTheRoad.crs' )

00:00.435: Course::LoadFromCRSFile( 'Courses/Samples/PlayersBest1-4.crs' )

00:00.435: Course::LoadFromCRSFile( 'Courses/Samples/PlayersBest13-16.crs' )

00:00.436: Course::LoadFromCRSFile( 'Courses/Samples/PlayersBest5-8.crs' )

00:00.436: Course::LoadFromCRSFile( 'Courses/Samples/PlayersBest9-12.crs' )

00:00.436: Course::LoadFromCRSFile( 'Courses/Samples/PlayersWorst.crs' )

00:00.437: Course::LoadFromCRSFile( 'Courses/Samples/Random Caprice.crs' )

00:00.437: Course::LoadFromCRSFile( 'Courses/Samples/StaminaTester.crs' )

00:00.457: Course::LoadFromCRSFile( 'Courses/Samples/Tortoise and the Hare.crs' )

00:00.478: Course::LoadFromCRSFile( 'Courses/Samples/Tournamix 4 Sample.crs' )

00:00.478: Course file 'Courses/Samples/Tournamix 4 Sample.crs' contains a fixed song entry 'Help me Dr. Dick' that does not exist. This entry will be ignored.

00:00.478: Course file 'Courses/Samples/Tournamix 4 Sample.crs' contains a fixed song entry 'DOO-BE-DI-BOY (KCP MIX)' that does not exist. This entry will be ignored.

00:00.478: Course file 'Courses/Samples/Tournamix 4 Sample.crs' contains a fixed song entry 'Laugh and Beats' that does not exist. This entry will be ignored.

00:00.478: Course file 'Courses/Samples/Tournamix 4 Sample.crs' contains a fixed song entry 'Baby Got Back' that does not exist. This entry will be ignored.

00:00.478: Course::LoadFromCRSFile( 'Courses/Samples/TrickyRandom.crs' )

00:00.487: underrun (10048 frames)

00:00.487: underrun (9984 frames)

00:00.487: underrun (9920 frames)

00:00.487: underrun (9856 frames)

00:00.487: underrun (9800 frames)

00:00.487: underrun (9736 frames)

00:00.487: underrun (9672 frames)

00:00.487: underrun (9608 frames)

00:00.487: underrun (9544 frames)

00:00.487: underrun (9480 frames)

00:00.487: underrun (9416 frames)

00:00.487: underrun (9360 frames)

00:00.487: underrun (9296 frames)

00:00.487: underrun (9232 frames)

00:00.487: underrun (9168 frames)

00:00.487: underrun (9104 frames)

00:00.487: underrun (9040 frames)

00:00.487: underrun (8976 frames)

00:00.487: underrun (8920 frames)

00:00.487: underrun (8856 frames)

00:00.487: underrun (8792 frames)

00:00.487: underrun (8728 frames)

00:00.487: underrun (8664 frames)

00:00.487: underrun (8600 frames)

00:00.487: underrun (8536 frames)

00:00.487: underrun (8472 frames)

00:00.487: underrun (8408 frames)

00:00.487: underrun (8344 frames)

00:00.487: underrun (8288 frames)

00:00.487: underrun (8224 frames)

00:00.487: underrun (8160 frames)

00:00.487: underrun (8096 frames)

00:00.487: underrun (8032 frames)

00:00.487: underrun (7968 frames)

00:00.488: underrun (7904 frames)

00:00.488: underrun (7840 frames)

00:00.488: underrun (7784 frames)

00:00.488: underrun (7720 frames)

00:00.488: underrun (7656 frames)

00:00.488: underrun (7592 frames)

00:00.488: underrun (7528 frames)

00:00.488: underrun (7464 frames)

00:00.488: underrun (7400 frames)

00:00.488: underrun (7336 frames)

00:00.488: underrun (7272 frames)

00:00.488: underrun (7216 frames)

00:00.488: underrun (7152 frames)

00:00.488: underrun (7088 frames)

00:00.488: underrun (7024 frames)

00:00.488: underrun (6960 frames)

00:00.488: underrun (6896 frames)

00:00.488: underrun (6832 frames)

00:00.488: underrun (6768 frames)

00:00.488: underrun (6712 frames)

00:00.488: underrun (6648 frames)

00:00.488: underrun (6584 frames)

00:00.488: underrun (6520 frames)

00:00.488: underrun (6456 frames)

00:00.488: underrun (6392 frames)

00:00.488: underrun (6328 frames)

00:00.488: underrun (6264 frames)

00:00.488: underrun (6208 frames)

00:00.488: underrun (6144 frames)

00:00.488: underrun (6080 frames)

00:00.488: underrun (6016 frames)

00:00.488: underrun (5952 frames)

00:00.488: underrun (5888 frames)

00:00.488: underrun (5824 frames)

00:00.488: underrun (5760 frames)

00:00.488: underrun (5696 frames)

00:00.488: underrun (5640 frames)

00:00.488: underrun (5576 frames)

00:00.488: underrun (5512 frames)

00:00.488: underrun (5448 frames)

00:00.488: underrun (5384 frames)

00:00.488: underrun (5320 frames)

00:00.488: underrun (5256 frames)

00:00.488: underrun (5192 frames)

00:00.488: underrun (5136 frames)

00:00.488: underrun (5072 frames)

00:00.489: underrun (5008 frames)

00:00.489: underrun (4952 frames)

00:00.489: underrun (4888 frames)

00:00.489: underrun (4824 frames)

00:00.489: underrun (4760 frames)

00:00.489: underrun (4696 frames)

00:00.489: underrun (4632 frames)

00:00.489: underrun (4568 frames)

00:00.489: underrun (4504 frames)

00:00.489: underrun (4440 frames)

00:00.489: underrun (4384 frames)

00:00.489: underrun (4320 frames)

00:00.489: underrun (4256 frames)

00:00.489: underrun (4192 frames)

00:00.489: underrun (4128 frames)

00:00.489: underrun (4064 frames)

00:00.489: underrun (4000 frames)

00:00.489: underrun (3936 frames)

00:00.489: underrun (3880 frames)

00:00.489: underrun (3816 frames)

00:00.489: underrun (3752 frames)

00:00.489: underrun (3688 frames)

00:00.489: underrun (3624 frames)

00:00.489: underrun (3560 frames)

00:00.489: underrun (3496 frames)

00:00.489: underrun (3432 frames)

00:00.489: underrun (3376 frames)

00:00.489: underrun (3312 frames)

00:00.489: underrun (3248 frames)

00:00.489: underrun (3184 frames)

00:00.489: underrun (3120 frames)

00:00.489: underrun (3056 frames)

00:00.489: underrun (2992 frames)

00:00.489: underrun (2928 frames)

00:00.489: underrun (2864 frames)

00:00.489: underrun (2808 frames)

00:00.489: underrun (2744 frames)

00:00.489: underrun (2680 frames)

00:00.489: underrun (2616 frames)

00:00.489: underrun (2552 frames)

00:00.489: underrun (2488 frames)

00:00.490: underrun (2424 frames)

00:00.490: underrun (2360 frames)

00:00.490: underrun (2304 frames)

00:00.490: underrun (2240 frames)

00:00.490: underrun (2176 frames)

00:00.490: underrun (2112 frames)

00:00.490: underrun (2048 frames)

00:00.490: underrun (1984 frames)

00:00.490: underrun (1920 frames)

00:00.490: underrun (1864 frames)

00:00.490: underrun (1800 frames)

00:00.490: underrun (1736 frames)

00:00.490: underrun (1672 frames)

00:00.490: underrun (1608 frames)

00:00.490: underrun (1544 frames)

00:00.490: underrun (1480 frames)

00:00.490: underrun (1416 frames)

00:00.490: underrun (1352 frames)

00:00.490: underrun (1288 frames)

00:00.490: underrun (1232 frames)

00:00.490: underrun (1168 frames)

00:00.490: underrun (1104 frames)

00:00.490: underrun (1040 frames)

00:00.490: underrun (976 frames)

00:00.490: underrun (912 frames)

00:00.490: underrun (848 frames)

00:00.490: underrun (784 frames)

00:00.490: underrun (728 frames)

00:00.490: underrun (664 frames)

00:00.490: underrun (600 frames)

00:00.490: underrun (536 frames)

00:00.490: underrun (472 frames)

00:00.490: underrun (408 frames)

00:00.490: underrun (344 frames)

00:00.490: underrun (280 frames)

00:00.490: underrun (224 frames)

00:00.490: underrun (160 frames)

00:00.490: underrun (96 frames)

00:00.490: underrun (32 frames)

00:00.501: Writing Data/Catalog.xml ...

00:00.530: Done.

00:00.532: RageSound::LoadSound( 'Themes/default/Sounds/MemoryCardManager ready.ogg' )

00:00.534: RageSound::LoadSound( 'Themes/default/Sounds/MemoryCardManager error.ogg' )

00:00.534: RageSound::LoadSound( 'Themes/default/Sounds/MemoryCardManager too late.ogg' )

00:00.535: RageSound::LoadSound( 'Themes/default/Sounds/MemoryCardManager disconnect.ogg' )

00:00.574: Profile::LoadAllFromDir( Data/MachineProfile/ )

00:00.575: Reading 'Data/MachineProfile/Editable.ini' failed: No such file or directory

00:00.575: Loading Data/MachineProfile/Stats.xml

00:00.575: Done.

00:00.575: UnlockSystem::Load()

00:00.642: underrun (2432 frames)

00:00.642: underrun (2376 frames)

00:00.642: underrun (2312 frames)

00:00.642: underrun (2248 frames)

00:00.642: underrun (2192 frames)

00:00.642: underrun (2128 frames)

00:00.642: underrun (2064 frames)

00:00.642: underrun (2000 frames)

00:00.642: underrun (1936 frames)

00:00.642: underrun (1872 frames)

00:00.642: underrun (1808 frames)

00:00.642: underrun (1744 frames)

00:00.642: underrun (1688 frames)

00:00.643: underrun (1624 frames)

00:00.643: underrun (1560 frames)

00:00.643: underrun (1496 frames)

00:00.643: underrun (1432 frames)

00:00.643: underrun (1368 frames)

00:00.643: underrun (1304 frames)

00:00.643: underrun (1240 frames)

00:00.643: underrun (1176 frames)

00:00.643: underrun (1112 frames)

00:00.643: underrun (1056 frames)

00:00.643: underrun (1000 frames)

00:00.643: underrun (944 frames)

00:00.643: underrun (880 frames)

00:00.643: underrun (816 frames)

00:00.643: underrun (752 frames)

00:00.643: underrun (688 frames)

00:00.643: underrun (624 frames)

00:00.643: underrun (560 frames)

00:00.643: underrun (496 frames)

00:00.643: underrun (440 frames)

00:00.643: underrun (376 frames)

00:00.643: underrun (312 frames)

00:00.643: underrun (248 frames)

00:00.643: underrun (184 frames)

00:00.643: underrun (120 frames)

00:00.643: underrun (56 frames)

00:00.644: Last seen video driver: OpenGL

00:00.644: Card matches 'OpenGL'.

00:00.644: Video renderers: 'opengl'

00:00.648: RageDisplay_OGL::RageDisplay_OGL()

00:00.963: underrun (64 frames)

00:01.592: SDL version: 1.2.11

00:01.592: Got 32 bpp (8880), 24 depth, 0 stencil

00:01.608: FPS: 1, CFPS 1, VPF: 0

00:01.608: OGL Vendor: NVIDIA Corporation

00:01.608: OGL Renderer: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!

00:01.608: OGL Version: 1.5.8 NVIDIA 96.39

00:01.608: OGL Extensions: GL_ARB_imaging GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum 

00:01.608: OGL Max texture size: 2048

00:01.608: GLU Version: 1.3

00:01.608: Display: :0.0 (screen 0)

00:01.608: Direct rendering: yes

00:01.608: X server vendor: The X.Org Foundation [1.3.0.0]

00:01.610: Server GLX vendor: NVIDIA Corporation [1.4]

00:01.610: Client GLX vendor: NVIDIA Corporation [1.4]

00:01.610: Fullscreen 640x480 16 color 16 texture 0Hz Vsync AA

00:01.610: RageInput::RageInput()

00:01.610: Found 0 joysticks

00:01.610: ScreenManager::ThemeChanged

00:01.610: RageSound::LoadSound( 'Themes/default/Sounds/Common start.ogg' )

00:01.619: RageSound::LoadSound( 'Themes/default/Sounds/Common coin.ogg' )

00:01.620: RageSound::LoadSound( 'Themes/default/Sounds/Common invalid.ogg' )

00:01.621: RageSound::LoadSound( 'Themes/default/Sounds/Common screenshot.ogg' )

00:01.622: RageSound::LoadSound( 'Themes/default/Sounds/Common back.ogg' )

00:01.647: glTexImage2D(format GL_COLOR_INDEX8_EXT, 128x32, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.648: RageBitmapTexture: Loaded 'Themes/default/Fonts/_japanese 16px [extra] 4x1.png' (128x32); FMT_PAL, source 128,32;  image 128,32.

00:01.661: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.662: RageBitmapTexture: Loaded 'Themes/default/Fonts/_japanese 16px [kanji 1] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.674: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.675: RageBitmapTexture: Loaded 'Themes/default/Fonts/_japanese 16px [kanji 2] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.687: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.687: RageBitmapTexture: Loaded 'Themes/default/Fonts/_japanese 16px [kanji 3] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.703: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.703: RageBitmapTexture: Loaded 'Themes/default/Fonts/_japanese 16px [kanji 4] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.719: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.720: RageBitmapTexture: Loaded 'Themes/default/Fonts/_japanese 16px [kanji 5] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.735: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.736: RageBitmapTexture: Loaded 'Themes/default/Fonts/_japanese 16px [kanji 6] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.783: glTexImage2D(format GL_COLOR_INDEX8_EXT, 512x512, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.784: RageBitmapTexture: Loaded 'Themes/default/Fonts/_japanese 16px [main] 16x16.png' (512x512); FMT_PAL, source 512,512;  image 512,512.

00:01.798: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.798: RageBitmapTexture: Loaded 'Themes/default/Fonts/_korean 16px [jamo 1] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.810: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.811: RageBitmapTexture: Loaded 'Themes/default/Fonts/_korean 16px [jamo 2] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.824: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.824: RageBitmapTexture: Loaded 'Themes/default/Fonts/_korean 16px [jamo 3] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.837: glTexImage2D(format GL_COLOR_INDEX8_EXT, 256x256, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:01.837: RageBitmapTexture: Loaded 'Themes/default/Fonts/_korean 16px [jamo 4] 8x8.png' (256x256); FMT_PAL, source 256,256;  image 256,256.

00:01.845: glTexImage2D(format GL_RGBA4, 256x128, format GL_RGBA, type GL_UNSIGNED_SHORT_4_4_4_4, pixfmt 1, imgpixfmt 1

00:01.845: RageBitmapTexture: Loaded 'Themes/default/Fonts/_misc 16px 8x4.png' (256x128); FMT_RGBA4, source 256,128;  image 256,128.

00:01.857: glTexImage2D(format GL_RGBA4, 512x32, format GL_RGBA, type GL_UNSIGNED_SHORT_4_4_4_4, pixfmt 1, imgpixfmt 1

00:01.857: RageBitmapTexture: Loaded 'Themes/default/Fonts/_game chars 16px 9x1.png' (512x32); FMT_RGBA4, source 288,32;  image 288,32.

00:01.859: glTexImage2D(format GL_RGBA4, 64x32, format GL_RGBA, type GL_UNSIGNED_SHORT_4_4_4_4, pixfmt 1, imgpixfmt 1

00:01.859: RageBitmapTexture: Loaded 'Themes/default/Fonts/Common default 2x1.png' (64x32); FMT_RGBA4, source 64,32;  image 64,32.

00:01.911: glTexImage2D(format GL_RGBA4, 512x512, format GL_RGBA, type GL_UNSIGNED_SHORT_4_4_4_4, pixfmt 1, imgpixfmt 1

00:01.911: RageBitmapTexture: Loaded 'Themes/default/Fonts/Common Normal 16x16.png' (512x512); FMT_RGBA4, source 512,512;  image 512,512.

00:01.943: glTexImage2D(format GL_RGBA4, 256x256, format GL_RGBA, type GL_UNSIGNED_SHORT_4_4_4_4, pixfmt 1, imgpixfmt 1

00:01.943: RageBitmapTexture: Loaded 'Themes/default/Fonts/ScreenManager credits 16x16.png' (256x256); FMT_RGBA4, source 256,256;  image 256,256.

00:01.945: Reading 'Data/Static.ini' failed: No such file or directory

00:01.946: ThemeManager::SwitchThemeAndLanguage: "default", "default"

00:01.950: GameState::EndGame

00:01.950: do the final mount

00:01.956: Reading 'Positioning.ini' failed: No such file or directory

00:01.957: Loading screen ScreenCompany

00:01.957: ScreenAttract::ScreenAttract(ScreenCompany)

00:01.957: GameState::EndGame

00:01.961: Reading 'Positioning.ini' failed: No such file or directory

00:01.965: Sprite::LoadFromTexture( Themes/default/BGAnimations/ScreenCompany background/white.png )

00:01.966: glTexImage2D(format GL_RGB5_A1, 8x8, format GL_RGBA, type GL_UNSIGNED_SHORT_5_5_5_1, pixfmt 2, imgpixfmt 2

00:01.966: RageBitmapTexture: Loaded 'Themes/default/BGAnimations/ScreenCompany background/white.png' (8x8); FMT_RGB5A1 opaque stretch, source 4,4;  image 8,8.

00:01.967: Sprite::LoadFromTexture( Themes/default/BGAnimations/ScreenCompany background/shadow (32bpp).png )

00:01.994: glTexImage2D(format GL_RGBA8, 512x512, format GL_RGBA, type GL_UNSIGNED_BYTE, pixfmt 0, imgpixfmt 0

00:01.994: RageBitmapTexture: Loaded 'Themes/default/BGAnimations/ScreenCompany background/shadow (32bpp).png' (512x512); FMT_RGBA8, source 512,284;  image 512,284.

00:01.995: Sprite::LoadFromTexture( Themes/default/BGAnimations/ScreenCompany background/stepmania (dither).png )

00:02.046: glTexImage2D(format GL_RGBA4, 512x256, format GL_RGBA, type GL_UNSIGNED_SHORT_4_4_4_4, pixfmt 1, imgpixfmt 1

00:02.046: RageBitmapTexture: Loaded 'Themes/default/BGAnimations/ScreenCompany background/stepmania (dither).png' (512x256); FMT_RGBA4 dither, source 480,252;  image 480,252.

00:02.050: Sprite::LoadFromTexture( Themes/default/BGAnimations/_black.png )

00:02.050: glTexImage2D(format GL_COLOR_INDEX8_EXT, 32x32, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:02.051: RageBitmapTexture: Loaded 'Themes/default/BGAnimations/_black.png' (32x32); FMT_PAL opaque, source 32,32;  image 32,32.

00:02.054: Sprite::LoadFromTexture( Themes/default/BGAnimations/_black.png )

00:02.056: Loaded ScreenCompany in 0.099032

00:02.056: ... SetFromNewScreen

00:02.071: RageSound::LoadSound( 'Themes/default/Sounds/ScreenCompany music.ogg' )

00:02.072: Sound "Themes/default/Sounds/ScreenCompany music.ogg" has a start time 0.000010 seconds in the past

00:02.089: XXX: deleting ''

00:03.059: FPS: 73, CFPS 73, VPF: 101

00:03.445: key: sym 13, key 130, state 1

00:04.247: ScreenAttract::AttractInput: go to ScreenTitleMenu

00:04.247: Loading screen ScreenTitleMenu

00:04.248: ScreenWithMenuElements::ScreenWithMenuElements()

00:04.264: glTexImage2D(format GL_RGBA4, 256x128, format GL_RGBA, type GL_UNSIGNED_SHORT_4_4_4_4, pixfmt 1, imgpixfmt 1

00:04.264: RageBitmapTexture: Loaded 'Themes/default/Numbers/MenuTimer 5x3.png' (256x128); FMT_RGBA4, source 160,102;  image 160,102.

00:04.265: RageSound::LoadSound( 'Themes/default/Sounds/MenuTimer tick.ogg' )

00:04.265: MenuElements::MenuElements()

00:04.266: Sprite::LoadFromTexture( Themes/default/BGAnimations/ScreenLogo background/1.png )

00:04.286: glTexImage2D(format GL_COLOR_INDEX8_EXT, 1024x512, format GL_COLOR_INDEX, type GL_UNSIGNED_BYTE, pixfmt 5, imgpixfmt 5

00:04.287: RageBitmapTexture: Loaded 'Themes/default/BGAnimations/ScreenLogo background/1.png' (1024x512); FMT_PAL opaque, source 640,480;  image 640,480.

00:04.288: Sprite::LoadFromTexture( Themes/default/Graphics/_blank.png )

00:04.289: glTexImage2D(format GL_RGB5_A1, 8x8, format GL_RGBA, type GL_UNSIGNED_SHORT_5_5_5_1, pixfmt 2, imgpixfmt 2

00:04.289: RageBitmapTexture: Loaded 'Themes/default/Graphics/_blank.png' (8x8); FMT_RGB5A1 matte stretch, source 2,2;  image 8,8.

00:04.289: Sprite::LoadFromTexture( Themes/default/Graphics/_blank.png )

00:04.291: Sprite::LoadFromTexture( Themes/default/BGAnimations/_black.png )

00:04.294: Sprite::LoadFromTexture( Themes/default/BGAnimations/_black.png )

00:04.297: Sprite::LoadFromTexture( Themes/default/BGAnimations/_black.png )

00:04.299: ScreenSelect::ScreenSelect()

00:04.302: ScreenTitleMenu::ScreenTitleMenu()

00:04.302: GameState::EndGame

00:04.306: Reading 'Positioning.ini' failed: No such file or directory

00:04.306: Sprite::LoadFromTexture( Themes/default/Graphics/ScreenLogo dance (dither).png )

00:04.375: glTexImage2D(format GL_RGBA4, 512x512, format GL_RGBA, type GL_UNSIGNED_SHORT_4_4_4_4, pixfmt 1, imgpixfmt 1

00:04.375: RageBitmapTexture: Loaded 'Themes/default/Graphics/ScreenLogo dance (dither).png' (512x512); FMT_RGBA4 dither, source 512,316;  image 512,316.

00:04.447: glTexImage2D(format GL_RGBA4, 512x512, format GL_RGBA, type GL_UNSIGNED_SHORT_4_4_4_4, pixfmt 1, imgpixfmt 1

00:04.447: RageBitmapTexture: Loaded 'Themes/default/Fonts/_shared1 16x16.png' (512x512); FMT_RGBA4, source 512,512;  image 512,512.

00:04.449: RageSound::LoadSound( 'Themes/default/Sounds/ScreenTitleMenu change.ogg' )

00:04.454: Loaded ScreenTitleMenu in 0.206921

00:04.454: ... SetFromNewScreen

00:04.455: RageSound::LoadSound( 'Themes/default/Sounds/_silent.ogg' )

00:04.456: Sound "Themes/default/Sounds/_silent.ogg" has a start time 0.000005 seconds in the past

00:04.459: XXX: deleting 'Themes/default/Sounds/ScreenCompany music.ogg'

00:04.459: XXX: deleting ''

00:04.459: ScreenAttract::~ScreenAttract()

00:04.459: Performing texture garbage collection.

00:04.460: 26 textures loaded:

00:04.460:  512x512 ( 0)                             shadow (32bpp).png

00:04.460:  256x512 ( 0)                             stepmania (dither).png

00:04.460:    8x  8 ( 0)                             white.png

00:04.460:  512x1024 ( 1)                            1.png

00:04.460:   32x 32 ( 3)                             _black.png

00:04.460:  512x512 ( 1)                             Common Normal 16x16.png

00:04.460:   32x 64 ( 4)                             Common default 2x1.png

00:04.460:  256x256 ( 1)                             ScreenManager credits 16x16.png

00:04.460:   32x512 ( 4)                             _game chars 16px 9x1.png

00:04.460:   32x128 ( 4)                             _japanese 16px [extra] 4x1.png

00:04.460:  256x256 ( 4)                             _japanese 16px [kanji 1] 8x8.png

00:04.460:  256x256 ( 4)                             _japanese 16px [kanji 2] 8x8.png

00:04.460:  256x256 ( 4)                             _japanese 16px [kanji 3] 8x8.png

00:04.460:  256x256 ( 4)                             _japanese 16px [kanji 4] 8x8.png

00:04.460:  256x256 ( 4)                             _japanese 16px [kanji 5] 8x8.png

00:04.460:  256x256 ( 4)                             _japanese 16px [kanji 6] 8x8.png

00:04.460:  512x512 ( 4)                             _japanese 16px [main] 16x16.png

00:04.460:  256x256 ( 4)                             _korean 16px [jamo 1] 8x8.png

00:04.460:  256x256 ( 4)                             _korean 16px [jamo 2] 8x8.png

00:04.460:  256x256 ( 4)                             _korean 16px [jamo 3] 8x8.png

00:04.460:  256x256 ( 4)                             _korean 16px [jamo 4] 8x8.png

00:04.460:  128x256 ( 4)                             _misc 16px 8x4.png

00:04.460:  512x512 ( 1)                             _shared1 16x16.png

00:04.460:  512x512 ( 1)                             ScreenLogo dance (dither).png

00:04.460:    8x  8 ( 2)                             _blank.png

00:04.460:  128x256 ( 1)                             MenuTimer 5x3.png

00:04.460: total 2776192 texels

00:04.460: key: sym 13, key 130, state 0

00:04.460: ScreenTitleMenu::Input( 0-130 )

00:04.502: key: sym 9, key 129, state 1

00:04.502: ScreenTitleMenu::Input( 0-129 )

00:04.605: ScreenTitleMenu::Input( 0-129 )

00:04.639: ScreenTitleMenu::Input( 0-129 )

00:04.661: ScreenTitleMenu::Input( 0-129 )

00:04.701: ScreenTitleMenu::Input( 0-129 )

00:04.725: ScreenTitleMenu::Input( 0-129 )

00:04.759: ScreenTitleMenu::Input( 0-129 )

00:04.799: ScreenTitleMenu::Input( 0-129 )

00:04.821: ScreenTitleMenu::Input( 0-129 )

00:04.845: ScreenTitleMenu::Input( 0-129 )

00:04.885: ScreenTitleMenu::Input( 0-129 )

00:04.919: ScreenTitleMenu::Input( 0-129 )

00:04.941: ScreenTitleMenu::Input( 0-129 )

00:04.981: key: sym 9, key 129, state 0

00:04.981: ScreenTitleMenu::Input( 0-129 )

00:05.079: key: sym 273, key 164, state 1

00:05.079: ScreenTitleMenu::Input( 0-164 )

00:05.223: key: sym 273, key 164, state 0

00:05.223: ScreenTitleMenu::Input( 0-164 )

00:05.303: key: sym 9, key 129, state 1

00:05.303: ScreenTitleMenu::Input( 0-129 )

00:05.391: key: sym 13, key 130, state 1

00:05.391: ScreenTitleMenu::Input( 0-130 )

00:05.395: ScreenTitleMenu::Input( 0-129 )

00:05.434: ScreenTitleMenu::Input( 0-129 )

00:05.458: FPS: 76, CFPS 76, VPF: 1180

00:05.458: ScreenTitleMenu::Input( 0-129 )

00:05.488: Loading screen ScreenExit

00:05.488: Loaded ScreenExit in 0.000108

00:05.488: ... SetFromNewScreen

00:05.488: ScreenTitleMenu::~ScreenTitleMenu()

00:05.489: ScreenSelect::~ScreenSelect()

00:05.490: Performing texture garbage collection.

00:05.490: 26 textures loaded:

00:05.490:  512x512 ( 0)                             shadow (32bpp).png

00:05.490:  256x512 ( 0)                             stepmania (dither).png

00:05.490:    8x  8 ( 0)                             white.png

00:05.490:  512x1024 ( 0)                            1.png

00:05.490:   32x 32 ( 0)                             _black.png

00:05.490:  512x512 ( 1)                             Common Normal 16x16.png

00:05.490:   32x 64 ( 2)                             Common default 2x1.png

00:05.490:  256x256 ( 1)                             ScreenManager credits 16x16.png

00:05.490:   32x512 ( 2)                             _game chars 16px 9x1.png

00:05.490:   32x128 ( 2)                             _japanese 16px [extra] 4x1.png

00:05.490:  256x256 ( 2)                             _japanese 16px [kanji 1] 8x8.png

00:05.490:  256x256 ( 2)                             _japanese 16px [kanji 2] 8x8.png

00:05.490:  256x256 ( 2)                             _japanese 16px [kanji 3] 8x8.png

00:05.490:  256x256 ( 2)                             _japanese 16px [kanji 4] 8x8.png

00:05.490:  256x256 ( 2)                             _japanese 16px [kanji 5] 8x8.png

00:05.490:  256x256 ( 2)                             _japanese 16px [kanji 6] 8x8.png

00:05.490:  512x512 ( 2)                             _japanese 16px [main] 16x16.png

00:05.490:  256x256 ( 2)                             _korean 16px [jamo 1] 8x8.png

00:05.490:  256x256 ( 2)                             _korean 16px [jamo 2] 8x8.png

00:05.490:  256x256 ( 2)                             _korean 16px [jamo 3] 8x8.png

00:05.490:  256x256 ( 2)                             _korean 16px [jamo 4] 8x8.png

00:05.490:  128x256 ( 2)                             _misc 16px 8x4.png

00:05.490:  512x512 ( 0)                             _shared1 16x16.png

00:05.490:  512x512 ( 0)                             ScreenLogo dance (dither).png

00:05.490:    8x  8 ( 0)                             _blank.png

00:05.490:  128x256 ( 0)                             MenuTimer 5x3.png

00:05.490: total 2776192 texels

00:05.494: XXX: deleting 'Themes/default/Sounds/_silent.ogg'

00:05.498: key: sym 13, key 130, state 0

00:05.916: ScreenExit: shutting down

00:05.916: GameState::EndGame

00:05.918: ScreenManager::~ScreenManager()

00:05.922: Shutting down music start thread ...

00:05.927: Music start thread shut down.

00:05.944: Shutting down mixer thread ...

00:05.944: Mixer thread shut down.

00:05.944: Shutting down decode thread ...

00:05.953: Decode thread shut down.

00:05.953: Mixing 491.765713 ahead in 3739 Mix() calls

00:06.250: Players joined: P1

00:06.250: Language: english

00:06.250: Current renderer: OpenGL

00:06.250: Theme: default

---

