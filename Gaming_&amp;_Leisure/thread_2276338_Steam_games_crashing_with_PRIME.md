---
title: "Steam games crashing with PRIME"
date: 2015-05-01
forum: Gaming &amp; Leisure
---

### Post by sebastian-meneses-n on 2015-05-01
Hello everyone.
I've been trying for months to get decent framerates on Ubuntu. Since that ugly bug that takes 100% of one cpu core when using AMD proprietary drivers, games are unplayable due to the heat generated.
Anyway, today I found that using the DRI_PRIME=1, after doing some tweaks to the system, allows to dinamically render stuff on your discrete GPU. I have an AMD/AMD hybrid graphics configuration.
The problem is, any time I try to run a game with DRI_PRIME=1 through steam, my xorg server crashes and I have to log back in. Sometimes the whole system dies. This doesn't happen when I don't use the DRI_PRIME command. I followed this steps: [http://forums.linuxmint.com/viewtopic.php?f=49&t=139413](http://forums.linuxmint.com/viewtopic.php?f=49&t=139413) wich are very similar to the ones found on the Arch Wiki.

I managed to save my steam output from terminal, and this is what happens before the game crashes:
```
Running Steam on ubuntu 14.04 64-bitSTEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1428965940)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steamwebhelper)/version(20150413151658)
Installing breakpad exception handler for appid(steamwebhelper)/version(1428938218)
Installing breakpad exception handler for appid(steamwebhelper)/version(20150413151658)
Installing breakpad exception handler for appid(steamwebhelper)/version(1428965940)
Installing breakpad exception handler for appid(steamwebhelper)/version(1428965940)
[0501/193411:ERROR:nss_util.cc(1018)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
FillInMachineIDInfo took a total of 0 milliseconds
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Generating new string page texture 2: 48x256, total string texture memory is 49,15 KB
Generating new string page texture 3: 384x256, total string texture memory is 442,37 KB
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Adding licenses for the following package(s): 0, 37, 1580, 2481, 2884, 4303, 7877, 8183, 8186, 11548, 14284, 16549, 16675, 21395, 21469, 26510, 27186, 29479, 30669, 30879, 36075, 37382, 42792, 45123, 49307, 62892, 62894, 62922, 62923, 62924, 62925, 62926, 62927, 62935, 63065, 63341, 63683, 64700, 64701, 66557, 66794
roaming config store loaded successfully - 4109 bytes.
migrating temporary roaming config store
ExecCommandLine: ""/home/sebastian/.local/share/Steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1428965940)
System startup time: 6,22 seconds
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
[0501/193417:ERROR:renderer_main.cc(227)] Running without renderer sandbox
Generating new string page texture 76: 256x256, total string texture memory is 704,51 KB
Generating new string page texture 77: 128x256, total string texture memory is 131,07 KB
Generating new string page texture 78: 128x256, total string texture memory is 835,58 KB
Generating new string page texture 79: 24x256, total string texture memory is 860,16 KB
Generating new string page texture 80: 64x256, total string texture memory is 925,70 KB
Installing breakpad exception handler for appid(steam)/version(1428965940)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Generating new string page texture 91: 256x256, total string texture memory is 393,22 KB
Generating new string page texture 109: 32x256, total string texture memory is 958,46 KB
Generating new string page texture 110: 128x256, total string texture memory is 1,09 MB
Generating new string page texture 112: 256x256, total string texture memory is 1,35 MB
Installing breakpad exception handler for appid(steam)/version(1428965940)
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/sebastian/.local/share/Steam/ubuntu12_32/steam-runtime
ExecCommandLine: "/home/sebastian/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
Installing breakpad exception handler for appid(steam)/version(1428965940)
saving roaming config store to 'sharedconfig.vdf'
roaming config store 2 saved successfully
Generating new string page texture 244: 256x256, total string texture memory is 1,61 MB
Game update: AppID 440 "Team Fortress 2", ProcID 17271, IP 0.0.0.0:0
ERROR: ld.so: object '/home/sebastian/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
locate: opción incorrecta -- «g»
Game removed: AppID 440 "Team Fortress 2", ProcID 17271 
Generating new string page texture 487: 128x256, total string texture memory is 1,74 MB
saving roaming config store to 'sharedconfig.vdf'
roaming config store 2 saved successfully
Installing breakpad exception handler for appid(steam)/version(1428965940)
Generating new string page texture 582: 8x256, total string texture memory is 1,75 MB
Generating new string page texture 583: 16x256, total string texture memory is 1,77 MB
Game update: AppID 440 "Team Fortress 2", ProcID 17463, IP 0.0.0.0:0
ERROR: ld.so: object '/home/sebastian/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/sebastian/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
pid 17466 != 17465, skipping destruction (fork without exec?)
ERROR: ld.so: object '/home/sebastian/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/sebastian/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
SDL video target is 'x11'
SDL video target is 'x11'
Installing breakpad exception handler for appid(gameoverlayui)/version(20150413151735)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Using Breakpad minidump system. Version: 2734753 AppID: 440
Setting breakpad minidump AppID = 440
Using breakpad crash handler
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198013316292 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198013316292
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Did not detect any valid joysticks.
 failed to dlopen /home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dbg.so error=/home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dbg.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen /home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dbg.so error=/home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dbg.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen stdshader_dbg.so error=stdshader_dbg.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen /home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx6.so error=/home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx6.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen /home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx6.so error=/home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx6.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen stdshader_dx6.so error=stdshader_dx6.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen /home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx7.so error=/home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx7.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen /home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx7.so error=/home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx7.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen stdshader_dx7.so error=stdshader_dx7.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen /home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx8.so error=/home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx8.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen /home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx8.so error=/home/sebastian/.local/share/Steam/steamapps/common/Team Fortress 2/bin/stdshader_dx8.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
 failed to dlopen stdshader_dx8.so error=stdshader_dx8.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
This system supports the OpenGL extension GL_EXT_framebuffer_object.
This system supports the OpenGL extension GL_EXT_framebuffer_blit.
This system supports the OpenGL extension GL_EXT_framebuffer_multisample.
This system DOES NOT support the OpenGL extension GL_APPLE_fence.
This system DOES NOT support the OpenGL extension GL_NV_fence.
This system supports the OpenGL extension GL_ARB_sync.
This system supports the OpenGL extension GL_EXT_draw_buffers2.
This system DOES NOT support the OpenGL extension GL_EXT_bindable_uniform.
This system DOES NOT support the OpenGL extension GL_APPLE_flush_buffer_range.
This system supports the OpenGL extension GL_ARB_map_buffer_range.
This system supports the OpenGL extension GL_ARB_vertex_buffer_object.
This system supports the OpenGL extension GL_ARB_occlusion_query.
This system DOES NOT support the OpenGL extension GL_APPLE_texture_range.
This system DOES NOT support the OpenGL extension GL_APPLE_client_storage.
This system DOES NOT support the OpenGL extension GL_ARB_uniform_buffer.
This system supports the OpenGL extension GL_ARB_vertex_array_bgra.
This system supports the OpenGL extension GL_EXT_vertex_array_bgra.
This system supports the OpenGL extension GL_ARB_framebuffer_object.
This system DOES NOT support the OpenGL extension GL_GREMEDY_string_marker.
This system supports the OpenGL extension GL_ARB_debug_output.
This system DOES NOT support the OpenGL extension GL_EXT_direct_state_access.
This system DOES NOT support the OpenGL extension GL_NV_bindless_texture.
This system DOES NOT support the OpenGL extension GL_AMD_pinned_memory.
This system supports the OpenGL extension GL_EXT_framebuffer_multisample_blit_scaled.
This system supports the OpenGL extension GL_EXT_texture_sRGB_decode.
This system DOES NOT support the OpenGL extension GL_NVX_gpu_memory_info.
This system DOES NOT support the OpenGL extension GL_ATI_meminfo.
This system supports the OpenGL extension GL_EXT_texture_compression_s3tc.
This system supports the OpenGL extension GL_EXT_texture_compression_dxt1.
This system supports the OpenGL extension GL_ANGLE_texture_compression_dxt3.
This system supports the OpenGL extension GL_ANGLE_texture_compression_dxt5.
This system supports the OpenGL extension GL_ARB_buffer_storage.
This system DOES NOT support the OpenGL extension GLX_EXT_swap_control_tear.
OpenGL: Gallium 0.4 on AMD OLAND 3.0 Mesa 10.3.2 (3.0.0)
GL_NV_bindless_texture: DISABLED
GL_AMD_pinned_memory: DISABLED
GL_ARB_buffer_storage: AVAILABLE
GL_EXT_texture_sRGB_decode: AVAILABLE
GL_NVX_gpu_memory_info: UNAVAILABLE
GL_ATI_meminfo: UNAVAILABLE
GL_MAX_SAMPLES_EXT: 8
CShaderDeviceMgrBase::GetRecommendedConfigurationInfo: CPU speed: 1600 MHz, Processor: AuthenticAMD
GlobalMemoryStatus: 4294967295
CShaderDeviceMgrBase::GetRecommendedConfigurationInfo: CPU speed: 1600 MHz, Processor: AuthenticAMD
GlobalMemoryStatus: 4294967295
IDirect3DDevice9::Create: BackBufWidth: 1920, BackBufHeight: 1080, D3DFMT: 3, BackBufCount: 1, MultisampleType: 0, MultisampleQuality: 0
GL sampler object usage: DISABLED


 ##### swap interval = 0     swap limit = 1 #####
Fatal IO error 11 (Recurso no disponible temporalmente) on X server :0.
XIO:  fatal IO error 11 (Recurso no disponible temporalmente) on X server ":0"
      after 1312 requests (1312 known processed) with 0 events remaining.
Missing shutdown function for DevShotGenerator_Init() : DevShotGenerator_Shutdown()
Missing shutdown function for MapReslistGenerator_Init() : MapReslistGenerator_Shutdown()
Missing shutdown function for COM_InitFilesystem( m_StartupInfo.m_pInitialMod ) : COM_ShutdownFileSystem()
Missing shutdown function for Steam3Client().Activate() : Steam3Client().Shutdown()
steamwebhelper: Fatal IO error 11 (Recurso no disponible temporalmente) on X server :0.
Assert( CClientPipe::BWriteAndReadResult: BWaitResult failed, disconnected ):/home/buildbot/buildslave/steam_rel_client_linux/build/src/clientdll/../common/pipes.cpp:730



```

By running the command DRI_PRIME=1 glxinfo | grep renderer shows that the adapter used is OLAND, codename for my discrete graphics card instead of ARUBA, the integrated one.
Even more, when actually running glxgears with PRIME:
[ATTACH=CONFIG]261702[/ATTACH]
You can actually check that the discrete card is on DynPwr state. This state turns to DynOff when I stop glxgears.

So I don't understand what's going on. DRI_PRIME=1 is able to render my 3d applications on my discrete card, but steam seems to fail at this.  I need some help to find out what's going on from the steam output I posted.

Thank you for your time!

---

