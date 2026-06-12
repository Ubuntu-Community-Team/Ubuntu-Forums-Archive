---
title: "[SOLVED] fglrx 8.8 and ETQW"
date: 2008-08-27
forum: Gaming &amp; Leisure
---

### Post by soxs on 2008-08-27
I just installed the latest and "greatest" fglrx driver.
In turn I couldn't run etqw anymore (extreme screen corruption).
So I decided to remove the .etqwcl folder.... which turned out to make it at least run again with 640x480@ultra_low_details (I am used to maxed settings :-S)
So I tried to increase screen res aswell as detail, but no matter what I did (changeing a single option and pressing the apply button) resulted in massive screen corruption.

Any ideas?

Google didn't spit out anything usefull...
Btw. I am running ubuntu_hardy_AMD64 kernel 2.6.24-21-generic
Hardware (Though that shouldn't really matter as long as it's above the minimum specs)
Phenom 9500
RadeonHD 3870 / fglrx 8.8
...

---

### Post by soxs on 2008-08-27
I found something related, but it didn't work for me :-S
[http://www.phoronix.com/forums/showthread.php?t=12322](http://www.phoronix.com/forums/showthread.php?t=12322)

---

### Post by soxs on 2008-08-30
anyone?
I got a new 4870 just some hours ago... though it didn't help aswell.

So does anyone get screen corruption when trying to change etqw resolution/any graphics realted options??


Note:
I allready got issues with 8.7, some game objects didn't get rendered correctly, I just got thousands of crazy coloured triangles, which made the game playabel again.
The last working driver for me was 8.6 (which I will revert to in case nobody has any answers handy)

---

### Post by soxs on 2008-09-12
terminal output:
```
ETQW 1.5.12663.12663  linux-x86 May  9 2008 13:57:26
found interface lo - loopback
found interface eth0 - 192.168.0.14/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /media/zer0/games/ETQW/base/game000.pk4 with checksum 0x3efd73a5
Loaded pk4 /media/zer0/games/ETQW/base/game001.pk4 with checksum 0xa02f1c18
Loaded pk4 /media/zer0/games/ETQW/base/game002.pk4 with checksum 0x87457e61
Loaded pk4 /media/zer0/games/ETQW/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /media/zer0/games/ETQW/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /media/zer0/games/ETQW/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /media/zer0/games/ETQW/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /media/zer0/games/ETQW/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /media/zer0/games/ETQW/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /media/zer0/games/ETQW/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /media/zer0/games/ETQW/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /media/zer0/games/ETQW/base/pak008.pk4 with checksum 0x71a93b80
Loaded pk4 /media/zer0/games/ETQW/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /media/zer0/games/ETQW/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /media/zer0/games/ETQW/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /media/zer0/games/ETQW/base/zpak_english003.pk4 with checksum 0xc2d7ed49
Loaded pk4 /media/zer0/games/ETQW/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /media/zer0/games/ETQW/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /media/zer0/games/ETQW/base/zpak_french003.pk4 with checksum 0x8f315c7b
Loaded pk4 /media/zer0/games/ETQW/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /media/zer0/games/ETQW/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /media/zer0/games/ETQW/base/zpak_german003.pk4 with checksum 0x370e6186
Loaded pk4 /media/zer0/games/ETQW/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /media/zer0/games/ETQW/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /media/zer0/games/ETQW/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /media/zer0/games/ETQW/base/zpak_korean003.pk4 with checksum 0x4f8dfac1
Loaded pk4 /media/zer0/games/ETQW/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /media/zer0/games/ETQW/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /media/zer0/games/ETQW/base/zpak_polish003.pk4 with checksum 0x8d9af876
Loaded pk4 /media/zer0/games/ETQW/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /media/zer0/games/ETQW/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /media/zer0/games/ETQW/base/zpak_russian003.pk4 with checksum 0x7e90b040
Loaded pk4 /media/zer0/games/ETQW/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /media/zer0/games/ETQW/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Loaded pk4 /media/zer0/games/ETQW/base/zpak_spanish003.pk4 with checksum 0xe7d989bc
Current search path:
$HOME/.etqwcl/base
/media/zer0/games/ETQW/base
/media/zer0/games/ETQW/base/zpak_spanish003.pk4 (6 files)
/media/zer0/games/ETQW/base/zpak_spanish002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_spanish001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_russian003.pk4 (5 files)
/media/zer0/games/ETQW/base/zpak_russian002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_russian001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_polish003.pk4 (6 files)
/media/zer0/games/ETQW/base/zpak_polish002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_polish001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_korean003.pk4 (5 files)
/media/zer0/games/ETQW/base/zpak_korean002.pk4 (12 files)
/media/zer0/games/ETQW/base/zpak_korean001.pk4 (12 files)
/media/zer0/games/ETQW/base/zpak_korean000.pk4 (6 files)
/media/zer0/games/ETQW/base/zpak_german003.pk4 (5 files)
/media/zer0/games/ETQW/base/zpak_german002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_german001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_french003.pk4 (14 files)
/media/zer0/games/ETQW/base/zpak_french002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_french001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_english003.pk4 (7 files)
/media/zer0/games/ETQW/base/zpak_english002.pk4 (117 files)
/media/zer0/games/ETQW/base/zpak_english001.pk4 (9 files)
/media/zer0/games/ETQW/base/zpak_english000.pk4 (1018 files)
/media/zer0/games/ETQW/base/pak008.pk4 (1496 files)
/media/zer0/games/ETQW/base/pak007.pk4 (1510 files)
/media/zer0/games/ETQW/base/pak006.pk4 (3 files)
/media/zer0/games/ETQW/base/pak005.pk4 (2172 files)
/media/zer0/games/ETQW/base/pak004.pk4 (72 files)
/media/zer0/games/ETQW/base/pak003.pk4 (1133 files)
/media/zer0/games/ETQW/base/pak002.pk4 (1637 files)
/media/zer0/games/ETQW/base/pak001.pk4 (1067 files)
/media/zer0/games/ETQW/base/pak000.pk4 (9350 files)
/media/zer0/games/ETQW/base/game002.pk4 (3 files)
/media/zer0/games/ETQW/base/game001.pk4 (11 files)
/media/zer0/games/ETQW/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Found $HOME/.etqwcl//etqw.pid - pid 7203
Removing stale lock file ($HOME/.etqwcl//etqw.pid)
----- Initializing Decls -----
Decompressing the global token cache...3566Kb
------------------------------
execing 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
execing 'autoexec.cfg'
Vendor: Device:
thread priority set to 1
couldn't exec '$HOME/.etqwcl/sdnet/_etqw_user_/base/autoexec.cfg'
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1920x1200
SDL_ListModes:
1920x1200 1920x1080 1680x1050 1600x1200 1440x900 1400x1050 1280x1024 1280x960 1280x768 1280x720 1152x864 
1024x768 800x600 720x480 640x480 640x400 512x384 400x300 320x240 320x200 
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports -5325672 - broken?
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
...using GL_EXT_texture_rectangle
...using GL_EXT_stencil_wrap
X..GL_EXT_stencil_two_side not found
...using GL_ATI_separate_stencil
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..GL_EXT_depth_bounds_test not found
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
...using GL_EXT_framebuffer_object
...using GL_EXT_packed_depth_stencil
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
...using GL_ARB_shader_objects
...using GL_ARB_vertex_shader
...using GL_ARB_fragment_shader
X..GL_ARB_fragment_program_shadow not found
...using GL_ARB_shadow
...using GL_ARB_depth_texture
...using GL_EXT_gpu_program_parameters
X..GL_EXT_timer_query not found
X..GL_GREMEDY_string_marker not found
X..GL_EXT_texture_compression_latc not found
---------- R_ARB2_Init ----------
Cg available.
---------------------------------
thread priority set to 2
thread priority set to 2
WARNING: vertex array range in virtual memory (SLOW)
renderSystem initialized.
--------------------------------------
72 strings read from localization/english/strings/bindings.lang
486 strings read from localization/english/strings/chat.lang
884 strings read from localization/english/strings/code.lang
2187 strings read from localization/english/strings/game.lang
3208 strings read from localization/english/strings/guis.lang
3384 strings read from localization/english/strings/lifestats.lang
3522 strings read from localization/english/strings/loadtips.lang
3861 strings read from localization/english/s
``` It exactly crashes there, right after the "s"

pending etqwcinfig.cfg:
```
seta r_AtmospherePostprocess "0"
seta r_noDoubleAtmosphere "1"
seta r_renderProgramLodFade "50"
seta r_renderProgramLodDistance "200"
seta r_occlusionsMaxFrames "10"
seta image_specularPicMip "1"
seta image_diffusePicMip "1"
seta image_bumpPicMip "1"
seta image_picMip "0"
seta image_picMipEnable "1"
seta image_detailPower "0.7"
seta image_ignoreHighQuality "0"
seta image_useBackgroundLoads "1"
seta image_useNormalCompression "2"
seta image_useAllFormats "1"
seta image_useCompression "1"
seta image_roundDown "1"
seta image_lodbias "0"
seta image_anisotropy "8"
seta image_filter "GL_LINEAR_MIPMAP_LINEAR"
seta r_MD5LodScale "3.4"
seta r_stuffCacheMegs "32"
seta r_skipStuff "0"
seta r_stuffFadeEnd "4500"
seta r_stuffFadeStart "4000"
seta r_useThreadedRenderer "0"
seta r_shaderSkipSpecCubeMaps "0"
seta r_normalizeNormalMaps "1"
seta r_shaderPreferALU "1"
seta r_shaderQuality "0"
seta r_useFBODestinationBuffer "0"
seta r_useAlphaToCoverage "1"
seta r_inhibitEXTGPP "0"
seta r_debugArrowStep "120"
seta r_debugLineWidth "1"
seta r_debugLineDepthTest "0"
seta r_skipRefractCopy "0"
seta r_skipDepthAmbient "0"
seta r_useShadowVisDistMult "1.0"
seta r_trisColor "1.0 1.0 1.0 1.0"
seta r_forceLoadImages "0"
seta r_megatexturePreferALU "1"
seta r_shadows "1"
seta r_shadowPolygonFactorMT "0"
seta r_shadowPolygonOffsetMT "-1"
seta r_shadowPolygonFactor "0"
seta r_shadowPolygonOffset "-1"
seta r_offsetunits "-600"
seta r_useDitherMask "1"
seta r_brightness "1"
seta r_gamma "1"
seta r_swapInterval "0"
seta r_elevateForceClear "1"
seta r_megaDrawMethod "3"
seta r_softParticles "0"
seta r_useIndexBuffers "0"
seta r_useShadowInfinite "1"
seta r_useShadowFastParallel "1"
seta r_imposterFade "80"
seta r_imposterFadeStart "130"
seta r_imposterCutoff "80"
seta r_visDistMult "1"
seta r_megaUpscale "0"
seta r_megaStreamFromDVD "0"
seta r_megaFadeTime "1500"
seta r_megaStreamBlocks "4"
seta r_detailFade "0.5"
seta r_detailTexture "1"
seta r_megaTilesPerSecond "9999"
seta r_customAspectRatioV "10"
seta r_customAspectRatioH "16"
seta r_aspectRatio "3"
seta r_customHeight "1024"
seta r_customWidth "1280"
seta r_fullscreen "1"
seta r_mode "3"
seta r_multiSamples "0"
seta com_unlockFPS "1"
seta com_useFastVidRestart "0"
seta com_videoRam "512"
seta com_showTPS "0"
seta com_showBPS "0"
seta com_showFPS "0"
seta com_allowConsole "1"
seta com_purgeAll "0"
seta com_gpuSpec "3"
seta com_machineSpec "2"
seta com_useBinaryDecls "2"
seta m_strafeSmooth "4"
seta m_smooth "1"
seta m_strafeScale "6.25"
seta m_yaw "0.022"
seta m_pitch "0.022"
seta sensitivity "5"
seta in_toggleSprint "0"
seta in_toggleRun "0"
seta in_freeLook "1"
seta in_anglespeedkey "1.5"
seta in_pitchspeed "140"
seta in_yawspeed "140"
seta net_clientRepeaterAutoDownload "0"
seta net_clientRepeaterDelay "0"
seta net_spawnRepeater "0"
seta net_httpServerPlayerBW "0"
seta net_httpServerGlobalBW "0"
seta net_httpServerPort "0"
seta net_httpProxyMode "1"
seta net_httpProxy ""
seta net_updateAutoExecute "1"
seta net_updateAutoDownload "1"
seta net_serverSpeexEnabled "1"
seta net_serverSpeexQuality "6"
seta net_serverPunkbusterEnabled "0"
seta net_clientPunkbusterEnabled "0"
seta net_clientUseroriginTime "100"
seta net_clientMaxRate "16000"
seta net_serverMaxClientRate "16000"
seta net_serverMaxRepeaterRate "32000"
seta ri_maxViewers "0"
seta in_joy4_device "0"
seta in_joy3_device "0"
seta in_joy2_device "0"
seta in_joy1_device "0"
seta sys_lang "english"
seta bse_simple "0"
seta bse_rateCost "1.0"
seta bse_rateLimit "1.0"
seta bse_detailLevel "1.0"
seta r_useSDLModes "1"
seta sys_videoRam "512"
seta s_decompressionLimit "6"
seta s_libOpenAL "libopenal.so.0"
seta s_micDevice ""
seta s_voiceDevice ""
seta s_primaryDevice ""
seta s_driver "alsa"
seta s_device "/dev/dsp"
seta s_noMic "0"
seta s_alsa_lib "libasound.so.2"
seta s_alsa_mic ""
seta s_alsa_pcm "default"
seta s_maxLowPrioritySounds "8"
seta s_useAdpcmCompression "1"
seta s_numberOfSpeakers "2"
seta s_globalFraction "0.8"
seta s_subFraction "0.75"
seta s_playDefaultSound "1"
seta s_volume_VoIPScale "0.5"
seta s_volume_VoIPOut_dB "0"
seta s_volume_VoIPIn_dB "0"
seta s_volume_dB "0"
seta s_meterTopTime "2000"
seta s_esa1_maxWindow "0.4"
seta s_esa1_minVolume "0.15"
seta s_earSeperationAlgo "0"
seta s_reverse "0"
seta s_spatializationDecay "2"
seta s_maxSoundsPerShader "0"
seta net_useUPnP "1"
seta net_QoSTimeout "999"
seta net_maxQoSRequests "12"
seta g_bind_context_anansi "vehicle"
seta g_bind_context_badger "vehicle"
seta g_bind_context_bumblebee "vehicle"
seta g_bind_context_desecrator "vehicle"
seta g_bind_context_goliath "vehicle"
seta g_bind_context_hog "vehicle"
seta g_bind_context_hornet "vehicle"
seta g_bind_context_husky "vehicle"
seta g_bind_context_icarus "vehicle"
seta g_bind_context_mcp "vehicle"
seta g_bind_context_platypus "vehicle"
seta g_bind_context_titan "vehicle"
seta g_bind_context_trojan "vehicle"
seta g_class_context_aggressor "aggressor"
seta g_class_context_technician "technician"
seta g_class_context_constructor "constructor"
seta g_class_context_oppressor "oppressor"
seta g_class_context_infiltrator "infiltrator"
seta g_class_context_soldier "soldier"
seta g_class_context_medic "medic"
seta g_class_context_engineer "engineer"
seta g_class_context_fieldops "fieldops"
seta g_class_context_covertops "covertops"
seta image_usePrecompressedTextures "1"
seta anim_reduced "0"
seta com_lastCPULevel "2"
seta com_lastCPUDetailLevel "2"
seta g_maxTransportDebrisExtraHigh "8"
seta g_maxTransportDebrisHigh "8"
seta g_maxTransportDebrisMedium "8"
seta g_maxTransportDebrisLow "8"
seta g_transportDebrisExtraHighCutoff "8192"
seta g_transportDebrisHighCutoff "4096"
seta g_transportDebrisMediumCutoff "2048"
seta g_transportDebrisLowCutoff "1024"
seta com_lastGraphicsLevel "2"
seta com_lastGraphicsDetailLevel "2"
seta com_lastLightingLevel "2"
seta com_lastFoliageLevel "2"
seta aor_physicsLod3StartScale "1"
seta aor_physicsLod2StartScale "1"
seta aor_physicsLod1StartScale "1"
seta aor_ikCutoffScale "1"
seta aor_animationCutoffScale "1"
seta aor_physicsCutoffScale "1"
seta g_cheapDecalsMaxDistance "16384"
seta g_buddyColor "0 1 1 1"
seta g_fireteamLeaderColor "1 1 0 1"
seta g_fireteamColor "1 1 1 1"
seta g_enemyColor "0.9 0.1 0.1 1"
seta g_neutralColor "0.75 0.75 0.75"
seta g_friendlyColor ".5 .83 0 1"
seta g_autoScreenshot "0"
seta g_autoScreenshotNameFormat "screenshots/scoreboard_$year$$month$$day$_$hour$$min$$sec$_$map$_$rules$_$name$_build_$srcrev$_$mediarev$.tga"
seta g_autoRecordDemos "0"
seta g_autoDemoNameFormat "$year$$month$$day$_$hour$$min$$sec$_$map$_$rules$_$name$_build_$srcrev$_$mediarev$.ndm"
seta g_useCompiledScript "1"
seta g_voteKeepVote "1"
seta g_minAutoVotePlayers "0"
seta g_votePassPercentage "51"
seta testLightColor "1.0 1.0 1.0"
seta g_noQuickChats "0"
seta g_aptWarning "3"
seta g_mineTriggerWarning "1"
seta g_drawHudMessages "1"
seta g_noTVChat "0"
seta ri_name ""
seta g_privateViewerPassword ""
seta ri_privateViewers "0"
seta g_repeaterPassword ""
seta g_viewerPassword ""
seta ri_useViewerPass "0"
seta g_drawVehicleIcons "1"
seta g_mineIconAlphaScale "1"
seta g_mineIconSize "10"
seta g_drawMineIcons "1"
seta net_serverDlTable ""
seta net_serverDlBaseURL ""
seta net_serverDownload "0"
seta g_keepFireTeamList "0"
seta g_tooltipVolumeScale "-20"
seta g_tooltipTimeScale "1"
seta g_playTooltipSound "2"
seta g_useBotsInPlayerTotal "1"
seta g_autoReadyWait "1"
seta g_autoReadyPercent "50"
seta g_maxVoiceChatsOver "30"
seta g_maxVoiceChats "4"
seta g_voteWait "2.5"
seta g_unlock_viewStyle "1"
seta g_unlock_interpolateMoving "1"
seta g_unlock_updateViewpos "1"
seta g_unlock_updateAngles "1"
seta g_maxSpectateTime "0"
seta g_kickBanLength "2"
seta g_xpSave "1"
seta g_privatePassword ""
seta g_password ""
seta g_gameReviewPause "0.09"
seta g_warmup "0.5"
seta g_muteSpecs "0"
seta g_warmupDamage "1"
seta g_teamSwitchDelay "5"
seta g_execMapConfigs "0"
seta g_complaintGUIDLimit "4"
seta g_complaintLimit "6"
seta g_allowComplaint_vehicles "1"
seta g_allowComplaint_explosives "1"
seta g_allowComplaint_charge "0"
seta g_allowComplaint_firesupport "1"
seta g_hitBeep "1"
seta g_weaponSwitchTimeout "1.5"
seta pm_vehicleSoundLerpScale "10"
seta password ""
seta g_maxPlayerWarnings "0"
seta g_advancedHud "0"
seta g_showPlayerShadow "1"
seta g_showPlayerClassIcon "0"
seta pm_skipBob "0"
seta pm_bobroll "0.002"
seta pm_bobpitch "0.002"
seta pm_bobup "0.005"
seta pm_runroll "0.005"
seta pm_runpitch "0.002"
seta pm_runbob "0.4"
seta pm_walkbob "0.3"
seta pm_crouchbob "0.23"
seta m_playerYawScale "1"
seta m_playerPitchScale "1"
seta m_heavyVehicleYawScale "1"
seta m_heavyVehiclePitchScale "1"
seta m_lightVehicleYawScale "1"
seta m_lightVehiclePitchScale "1"
seta m_bumblebeeYawScale "1"
seta m_bumblebeePitchScale "1"
seta m_helicopterYawScale "1"
seta m_helicopterPitchScale "1"
seta m_helicopterYaw "0.022"
seta m_helicopterPitch "-0.022"
seta g_commandMapZoom "0.25"
seta g_commandMapZoomStep "0.125"
seta g_decals "1"
seta ui_swapFlightYawAndRoll "0"
seta ui_showComplaints "1"
seta ui_voipReceiveFireTeam "1"
seta ui_voipReceiveTeam "1"
seta ui_voipReceiveGlobal "0"
seta ui_drivingCameraFreelook "0"
seta ui_rememberCameraMode "0"
seta ui_advancedFlightControls "0"
seta ui_postArmFindBestWeapon "0"
seta ui_ignoreExplosiveWeapons "1"
seta ui_autoSwitchEmptyWeapons "1"
seta ui_showGun "1"
seta ui_clanTagPosition "0"
seta ui_clanTag ""
seta ui_name "soxs"
seta si_serverURL ""
seta si_gameReviewReadyWait "1"
seta si_disableGlobalChat "0"
seta si_noProficiency "0"
seta si_allowLateJoin "1"
seta si_minPlayers "0"
seta si_readyPercent "51"
seta si_disableVoting "1"
seta si_adminStart "0"
seta si_motd_4 ""
seta si_motd_3 ""
seta si_motd_2 ""
seta si_motd_1 ""
seta si_irc ""
seta si_email ""
seta si_adminname ""
seta si_website ""
seta si_teamForceBalance "0"
seta si_timelimit "30"
seta si_rules "sdGameRulesObjective"
seta si_spectators "1"
seta si_pure "1"
seta si_needPass "0"
seta si_teamDamage "0"
seta si_privateClients "0"
seta si_maxPlayers "16"
seta si_name "ETQW Server"
seta g_showVehicleCockpits "1"
seta g_vehicleSteerKeyScale "1"
seta g_radialMenuMouseInput "2"
seta in_hovertank_side_power "1"
seta in_hovertank_side_offset "0"
seta in_hovertank_side_invert "0"
seta in_hovertank_side_speed "140"
seta in_hovertank_side_deadZone "0.2"
seta in_hovertank_side_axis "-1"
seta in_hovertank_side_joy "1"
seta in_hovertank_yaw_power "4"
seta in_hovertank_yaw_offset "0"
seta in_hovertank_yaw_invert "1"
seta in_hovertank_yaw_speed "230"
seta in_hovertank_yaw_deadZone "0.2"
seta in_hovertank_yaw_axis "2"
seta in_hovertank_yaw_joy "1"
seta in_hovertank_pitch_power "4"
seta in_hovertank_pitch_offset "0"
seta in_hovertank_pitch_invert "1"
seta in_hovertank_pitch_speed "230"
seta in_hovertank_pitch_deadZone "0.2"
seta in_hovertank_pitch_axis "3"
seta in_hovertank_pitch_joy "1"
seta in_hovertank_turn_power "1"
seta in_hovertank_turn_offset "0"
seta in_hovertank_turn_invert "0"
seta in_hovertank_turn_speed "140"
seta in_hovertank_turn_deadZone "0.2"
seta in_hovertank_turn_axis "0"
seta in_hovertank_turn_joy "1"
seta in_hovertank_forward_power "1"
seta in_hovertank_forward_offset "0"
seta in_hovertank_forward_invert "1"
seta in_hovertank_forward_speed "140"
seta in_hovertank_forward_deadZone "0.2"
seta in_hovertank_forward_axis "1"
seta in_hovertank_forward_joy "1"
seta in_heli_side_power "1"
seta in_heli_side_offset "0"
seta in_heli_side_invert "1"
seta in_heli_side_speed "140"
seta in_heli_side_deadZone "0.2"
seta in_heli_side_axis "2"
seta in_heli_side_joy "1"
seta in_heli_forward_power "1"
seta in_heli_forward_offset "0"
seta in_heli_forward_invert "0"
seta in_heli_forward_speed "140"
seta in_heli_forward_deadZone "0.2"
seta in_heli_forward_axis "3"
seta in_heli_forward_joy "1"
seta in_heli_yaw_power "1"
seta in_heli_yaw_offset "0"
seta in_heli_yaw_invert "0"
seta in_heli_yaw_speed "140"
seta in_heli_yaw_deadZone "0.2"
seta in_heli_yaw_axis "0"
seta in_heli_yaw_joy "1"
seta in_heli_throttle_power "1"
seta in_heli_throttle_offset "0"
seta in_heli_throttle_invert "1"
seta in_heli_throttle_speed "140"
seta in_heli_throttle_deadZone "0.2"
seta in_heli_throttle_axis "1"
seta in_heli_throttle_joy "1"
seta in_car_yaw_power "4"
seta in_car_yaw_offset "0"
seta in_car_yaw_invert "1"
seta in_car_yaw_speed "230"
seta in_car_yaw_deadZone "0.2"
seta in_car_yaw_axis "2"
seta in_car_yaw_joy "1"
seta in_car_pitch_power "4"
seta in_car_pitch_offset "0"
seta in_car_pitch_invert "1"
seta in_car_pitch_speed "230"
seta in_car_pitch_deadZone "0.2"
seta in_car_pitch_axis "3"
seta in_car_pitch_joy "1"
seta in_car_steering_power "1"
seta in_car_steering_offset "0"
seta in_car_steering_invert "0"
seta in_car_steering_speed "140"
seta in_car_steering_deadZone "0.2"
seta in_car_steering_axis "0"
seta in_car_steering_joy "1"
seta in_car_throttle_power "1"
seta in_car_throttle_offset "0"
seta in_car_throttle_invert "1"
seta in_car_throttle_speed "140"
seta in_car_throttle_deadZone "0.2"
seta in_car_throttle_axis "1"
seta in_car_throttle_joy "1"
seta in_player_side_power "1"
seta in_player_side_offset "0"
seta in_player_side_invert "0"
seta in_player_side_speed "140"
seta in_player_side_deadZone "0.2"
seta in_player_side_axis "0"
seta in_player_side_joy "1"
seta in_player_forward_power "1"
seta in_player_forward_offset "0"
seta in_player_forward_invert "1"
seta in_player_forward_speed "140"
seta in_player_forward_deadZone "0.2"
seta in_player_forward_axis "1"
seta in_player_forward_joy "1"
seta in_player_yaw_power "4"
seta in_player_yaw_offset "0"
seta in_player_yaw_invert "1"
seta in_player_yaw_speed "230"
seta in_player_yaw_deadZone "0.2"
seta in_player_yaw_axis "2"
seta in_player_yaw_joy "1"
seta in_player_pitch_power "4"
seta in_player_pitch_offset "0"
seta in_player_pitch_invert "1"
seta in_player_pitch_speed "230"
seta in_player_pitch_deadZone "0.2"
seta in_player_pitch_axis "3"
seta in_player_pitch_joy "1"
seta g_playerIconAlphaScale "0.5"
seta g_playerArrowIconSize "10"
seta g_playerIconSize "20"
seta g_drawPlayerIcons "1"
seta g_noBotSpectate "0"
seta g_spectateViewLerpScale "0.7"
seta g_rotateCommandMap "1"
seta net_clientLagOMeter "0"
seta g_waypointDistanceMax "3084"
seta g_waypointDistanceMin "512"
seta g_waypointSizeMax "32"
seta g_waypointSizeMin "16"
seta g_showWayPoints "1"
seta g_waypointAlphaScale "0.7"
seta g_radialMenuMouseSensitivity "0.5"
seta g_radialMenuUseNumberShortcuts "1"
seta g_radialMenuStyle "0"
seta gui_invertMenuPitch "0"
seta gui_doubleClickTime "0.2"
seta gui_tooltipDelay "0.7"
seta gui_showRespawnText "1"
seta gui_vehicleDirectionAlpha "0.5"
seta gui_vehicleAlpha "1"
seta gui_tooltipAlpha "1"
seta gui_voteAlpha "1"
seta gui_obitAlpha "1"
seta gui_objectiveStatusAlpha "1"
seta gui_personalBestsAlpha "1"
seta gui_objectiveListAlpha "1"
seta gui_commandMapAlpha "1"
seta gui_fireTeamAlpha "1"
seta gui_chatAlpha "1"
seta gui_crosshairColor "1 1 1 1"
seta gui_crosshairSpreadScale "1"
seta gui_crosshairGrenadeAlpha "0.5"
seta gui_crosshairStatsAlpha "0"
seta gui_crosshairSpreadAlpha "0.5"
seta gui_crosshairAlpha "0.5"
seta gui_crosshairKey "pin_01"
seta gui_crosshairDef "crosshairs"
seta g_skipIntro "0"
seta s_volumeMusic_dB "0"
seta gui_notificationPause "5"
seta gui_notificationTime "8"
seta g_chatLineTimeout "5"
seta g_chatFireTeamColor "0.8 0.8 0.8 1"
seta g_chatTeamColor "1 1 0 1"
seta g_chatDefaultColor "1 1 1 1"
```

---

### Post by artkochermin on 2008-09-12
Hi soxs,

I wonder how you installed your driver. Btw your kernel is a bit newer than mine. In any case, the crash looks odd. I looked at my terminal output and, although there are few differences, this one stands out more:

---------- R_ARB2_Init ----------
Cg available.
---------------------------------
thread priority set to 2
thread priority set to 2
using ARB_vertex_buffer_object memory
renderSystem initialized.

Yours is different somehow. Can you actually get the game to start with all settings set to low or by removing the config file?

---

### Post by soxs on 2008-09-12
After removing .etqwcl via ```
rm -Rvf $HOME/.etqwcl
``` I get this, (well it just crashes about the same time)
```
ETQW 1.5.12663.12663  linux-x86 May  9 2008 13:57:26
found interface lo - loopback
found interface eth0 - xxx.yyy.zzz.???/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /media/zer0/games/ETQW/base/game000.pk4 with checksum 0x3efd73a5
Loaded pk4 /media/zer0/games/ETQW/base/game001.pk4 with checksum 0xa02f1c18
Loaded pk4 /media/zer0/games/ETQW/base/game002.pk4 with checksum 0x87457e61
Loaded pk4 /media/zer0/games/ETQW/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /media/zer0/games/ETQW/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /media/zer0/games/ETQW/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /media/zer0/games/ETQW/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /media/zer0/games/ETQW/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /media/zer0/games/ETQW/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /media/zer0/games/ETQW/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /media/zer0/games/ETQW/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /media/zer0/games/ETQW/base/pak008.pk4 with checksum 0x71a93b80
Loaded pk4 /media/zer0/games/ETQW/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /media/zer0/games/ETQW/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /media/zer0/games/ETQW/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /media/zer0/games/ETQW/base/zpak_english003.pk4 with checksum 0xc2d7ed49
Loaded pk4 /media/zer0/games/ETQW/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /media/zer0/games/ETQW/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /media/zer0/games/ETQW/base/zpak_french003.pk4 with checksum 0x8f315c7b
Loaded pk4 /media/zer0/games/ETQW/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /media/zer0/games/ETQW/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /media/zer0/games/ETQW/base/zpak_german003.pk4 with checksum 0x370e6186
Loaded pk4 /media/zer0/games/ETQW/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /media/zer0/games/ETQW/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /media/zer0/games/ETQW/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /media/zer0/games/ETQW/base/zpak_korean003.pk4 with checksum 0x4f8dfac1
Loaded pk4 /media/zer0/games/ETQW/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /media/zer0/games/ETQW/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /media/zer0/games/ETQW/base/zpak_polish003.pk4 with checksum 0x8d9af876
Loaded pk4 /media/zer0/games/ETQW/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /media/zer0/games/ETQW/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /media/zer0/games/ETQW/base/zpak_russian003.pk4 with checksum 0x7e90b040
Loaded pk4 /media/zer0/games/ETQW/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /media/zer0/games/ETQW/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Loaded pk4 /media/zer0/games/ETQW/base/zpak_spanish003.pk4 with checksum 0xe7d989bc
Current search path:
/home/bernhard/.etqwcl/base
/media/zer0/games/ETQW/base
/media/zer0/games/ETQW/base/zpak_spanish003.pk4 (6 files)
/media/zer0/games/ETQW/base/zpak_spanish002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_spanish001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_russian003.pk4 (5 files)
/media/zer0/games/ETQW/base/zpak_russian002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_russian001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_polish003.pk4 (6 files)
/media/zer0/games/ETQW/base/zpak_polish002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_polish001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_korean003.pk4 (5 files)
/media/zer0/games/ETQW/base/zpak_korean002.pk4 (12 files)
/media/zer0/games/ETQW/base/zpak_korean001.pk4 (12 files)
/media/zer0/games/ETQW/base/zpak_korean000.pk4 (6 files)
/media/zer0/games/ETQW/base/zpak_german003.pk4 (5 files)
/media/zer0/games/ETQW/base/zpak_german002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_german001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_french003.pk4 (14 files)
/media/zer0/games/ETQW/base/zpak_french002.pk4 (119 files)
/media/zer0/games/ETQW/base/zpak_french001.pk4 (13 files)
/media/zer0/games/ETQW/base/zpak_english003.pk4 (7 files)
/media/zer0/games/ETQW/base/zpak_english002.pk4 (117 files)
/media/zer0/games/ETQW/base/zpak_english001.pk4 (9 files)
/media/zer0/games/ETQW/base/zpak_english000.pk4 (1018 files)
/media/zer0/games/ETQW/base/pak008.pk4 (1496 files)
/media/zer0/games/ETQW/base/pak007.pk4 (1510 files)
/media/zer0/games/ETQW/base/pak006.pk4 (3 files)
/media/zer0/games/ETQW/base/pak005.pk4 (2172 files)
/media/zer0/games/ETQW/base/pak004.pk4 (72 files)
/media/zer0/games/ETQW/base/pak003.pk4 (1133 files)
/media/zer0/games/ETQW/base/pak002.pk4 (1637 files)
/media/zer0/games/ETQW/base/pak001.pk4 (1067 files)
/media/zer0/games/ETQW/base/pak000.pk4 (9350 files)
/media/zer0/games/ETQW/base/game002.pk4 (3 files)
/media/zer0/games/ETQW/base/game001.pk4 (11 files)
/media/zer0/games/ETQW/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3566Kb
------------------------------
couldn't exec 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
couldn't exec 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
/proc/cpuinfo CPU frequency: 1100 MHz
parse /proc/cpuinfo for CPU information
4 logical, 1 physical CPU(s)
detecting video ram (set sys_videoRam on command line to override) ..
trying /proc/dri/0/umm
guess failed, return default low-end VRAM setting ( 128MB VRAM )
Detected
 	1 1.10 GHz CPU
	3968 MB of System memory
	128 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1920x1200
execing 'specs/minspec.dat'
execing 'specs/minspec_cpu.dat'
execing 'specs/minspec_gamedetail.dat'
execing 'specs/minspec_gpu.dat'
execing 'specs/minspec_gpudetail.dat'
execing 'specs/minspec_lighting.dat'
execing 'specs/minspec_foliage.dat'
Vendor: Device:
execing 'specs/minspec_foliage.dat'
thread priority set to 1
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
SDL_ListModes:
1920x1200 1920x1080 1680x1050 1600x1200 1440x900 1400x1050 1280x1024 1280x960 1280x768 1280x720 1152x864 
1024x768 800x600 720x480 640x480 640x400 512x384 400x300 320x240 320x200 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: SDL reports -965016 - broken?
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
...using GL_EXT_texture_rectangle
...using GL_EXT_stencil_wrap
X..GL_EXT_stencil_two_side not found
...using GL_ATI_separate_stencil
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..GL_EXT_depth_bounds_test not found
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
...using GL_EXT_framebuffer_object
...using GL_EXT_packed_depth_stencil
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
...using GL_ARB_shader_objects
...using GL_ARB_vertex_shader
...using GL_ARB_fragment_shader
X..GL_ARB_fragment_program_shadow not found
...using GL_ARB_shadow
...using GL_ARB_depth_texture
...using GL_EXT_gpu_program_parameters
X..GL_EXT_timer_query not found
X..GL_GREMEDY_string_marker not found
X..GL_EXT_texture_compression_latc not found
---------- R_ARB2_Init ----------
Cg available.
---------------------------------
thread priority
```


May you plx attach the output from ```
cat /etc/X11/xorg.conf
``` maybe I adde a "bad" option which makes baheave etqw like it does?

Btw. atm I can't even access the menu.. it just crashes before..

I installed my driver via the installer created debian packages..

---

### Post by artkochermin on 2008-09-12
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

I wouldn't rely on it 100%, since I just tried installing catalyst with --buildpkg Ubuntu/hardy. Although the game still works, somehow etqw registers only 128MB of memory. I didn't test the game that well yet. I want to see if I get some corruption that I used to get after playing for few hours. Yeah, these drivers are not that good yet....

---

### Post by artkochermin on 2008-09-12
btw, you have 4Gigs of memory. Do you have remapping enabled in your bios. Although I might be totally wrong, it could be another place to look for the solution.

---

### Post by soxs on 2008-09-12
> **artkochermin said:**
> btw, you have 4Gigs of memory. Do you have remapping enabled in your bios. Although I might be totally wrong, it could be another place to look for the solution.

If my f*** bios had such an option I would do that, but it unfourtnatly doesn't -.-

I will install the drivers via the installer itself, no packages this time, I will do that tomorrow... I am tired of messing up my Pc the second time today *g*
thx for your effort so far

btw, does etqw detect your vram correctly if not installing the driver via pkgs?

---

### Post by artkochermin on 2008-09-12
Hope that's not the problem. So, how did you install your ATI drivers. What procedure did you follow??? You mentioned that you edited your xorg.conf file. Did the game work with default one(the one you got after you installed ATI drivers)?

Artur

---

### Post by artkochermin on 2008-09-12
> **soxs said:**
> If my f*** bios had such an option I would do that, but it unfourtnatly doesn't -.-

I will install the drivers via the installer itself, no packages this time, I will do that tomorrow... I am tired of messing up my Pc the second time today *g*
thx for your effort so far

btw, does etqw detect your vram correctly if not installing the driver via pkgs?

My memory was detected correctly with 8.8 driver when I just followed ATI instructions(sh ati-driver-installer-8-8-x86.x86_64.run ). After I tried building Ubuntu package today and installing it, the game only detects 128, but works as fast with same FPS(from what I can tell in few minutes of testing it).

---

### Post by soxs on 2008-09-12
> **artkochermin said:**
> Hope that's not the problem. So, how did you install your ATI drivers. What procedure did you follow??? You mentioned that you edited your xorg.conf file. Did the game work with default one(the one you got after you installed ATI drivers)?

Artur

I never really stopped with the default aticonfig --initial stuff, I learned what settings had which effect and used them as far as my knowledge allowed me to use them...

Ok, I just got over the process Dling the 8.8 driver suite for th last time today...
brb after installing and rebooting...

**EDIT:**
I reseted my xorg.conf settings plus reinstalled 8.8 without the usage of deb pkgs, the driver itself still works, but etqw seems to be totally broken:
```

./etqw-rthread.x86: error while loading shared libraries: libSDL-1.2.id.so.0: cannot open shared object file: No such file or directory

```

---

### Post by soxs on 2008-09-12
OMG -.- I got it:
my starter looked like this:
```
#!/bin/bash
SDL_VIDEO_X11_DGAMOUSE=0
SDL_MOUSE_RELATIVE=0
cd /media/zer0/games/ETQW
taskset -c 1,2,3 ./etqw-threaded.x86

```
which in general isn't that wrong, but it seems to make a diffrence if i do it like that or like that (which actually works!!):
```
/etqw/games/folder/etqw
``` where [COLOR="Red"]etqw[/COLOR] is the excutable file..

so thanks a lot for putting my nose onto that again^^
_SOLVED_

---

### Post by artkochermin on 2008-09-12
Awesome!!!

---

