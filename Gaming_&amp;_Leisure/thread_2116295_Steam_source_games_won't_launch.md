---
title: "Steam source games won't launch"
date: 2013-02-15
forum: Gaming &amp; Leisure
---

### Post by amkxxx on 2013-02-15
Hi,
tried steam support but never got any reply.
Since steam finally came to beloved Ubuntu I wanted to test it. I tried to run Team Fortress 2 but after "Prepairing to launch" window the screen goes black and then back to steam like nothing happened.
I'm using Ubuntu 12.10 with fglrx-updates AMD driver
Intel Pentium Dual Core 2 Ghz, 2GB RAM ati mobility radeon hd5470
please help

here's some terminal output I copied, but don't understand much of it:

Running Steam on ubuntu 12.10 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
unlinked 0 orphaned pipes
Gtk-Message: Failed to load module "overlay-scrollbar"
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
[0215/180357:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311.30 KB
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Adding license for package 0
Adding license for package 1
Adding license for package 11
Adding license for package 164
Adding license for package 2294
Adding license for package 2621
Adding license for package 16222
Adding license for package 17250
Adding license for package 17634
roaming config store loaded successfully - 2379 bytes.
migrating temporary roaming config store
ExecCommandLine: "/home/amk/.local/share/Steam/ubuntu12_32/steam"
`menu_proxy_module_load': /home/amk/.local/share/Steam/ubuntu12_32/steam: undefined symbol: menu_proxy_module_load

(steam:5463): Gtk-WARNING **: Failed to load type module: (null)

Generating new string page texture 70: 1024x256, total string texture memory is 1.36 MB
Generating new string page texture 71: 128x256, total string texture memory is 1.49 MB
Generating new string page texture 72: 128x256, total string texture memory is 131.07 KB
Generating new string page texture 73: 64x256, total string texture memory is 1.56 MB
Generating new string page texture 74: 32x256, total string texture memory is 1.59 MB

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Generating new string page texture 77: 128x256, total string texture memory is 1.72 MB
Generating new string page texture 78: 512x256, total string texture memory is 2.24 MB
Generating new string page texture 85: 384x256, total string texture memory is 2.64 MB
System startup time: 12.84 seconds
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Running Steam on ubuntu 12.10 32-bit
STEAM_RUNTIME has been set by the user to: /home/amk/.local/share/Steam/ubuntu12_32/steam-runtime
ExecCommandLine: "/home/amk/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 112: 128x256, total string texture memory is 2.77 MB
Game update: AppID 440 "Team Fortress 2", ProcID 5582, IP 0.0.0.0:0

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:5463): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
saving roaming config store to 'sharedconfig.vdf'
roaming config store 2 saved successfully
SDL video target is 'x11'
SDL video target is 'x11'
This system supports the OpenGL extension GL_EXT_framebuffer_object.
This system supports the OpenGL extension GL_EXT_framebuffer_blit.
This system supports the OpenGL extension GL_EXT_framebuffer_multisample.
This system DOES NOT support the OpenGL extension GL_APPLE_fence.
This system DOES NOT support the OpenGL extension GL_NV_fence.
This system supports the OpenGL extension GL_ARB_sync.
This system supports the OpenGL extension GL_EXT_draw_buffers2.
This system supports the OpenGL extension GL_EXT_bindable_uniform.
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
This system DOES NOT support the OpenGL extension GL_ARB_debug_output.
This system supports the OpenGL extension GL_EXT_direct_state_access.
This system DOES NOT support the OpenGL extension GL_NV_bindless_texture.
This system supports the OpenGL extension GL_AMD_pinned_memory.
This system DOES NOT support the OpenGL extension GL_EXT_framebuffer_multisample_blit_scaled.
This system supports the OpenGL extension GL_EXT_texture_sRGB_decode.
This system DOES NOT support the OpenGL extension GL_NVX_gpu_memory_info.
This system supports the OpenGL extension GL_ATI_meminfo.
This system supports the OpenGL extension GL_EXT_texture_compression_s3tc.
This system DOES NOT support the OpenGL extension GLX_EXT_swap_control_tear.
GL_NV_bindless_texture: DISABLED
GL_AMD_pinned_memory: DISABLED
GL_EXT_texture_sRGB_decode: AVAILABLE
Installing breakpad exception handler for appid(gameoverlayui)/version(20130214025819_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Using breakpad crash handler
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Gtk-Message: Failed to load module "overlay-scrollbar"
[0215/180425:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Setting breakpad minidump AppID = 440
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561197970878275 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561197970878275
Did not detect any valid joysticks.
GL_NVX_gpu_memory_info: UNAVAILABLE
GL_ATI_meminfo: AVAILABLE
GL_ATI_meminfo: GL_TEXTURE_FREE_MEMORY_ATI: Total Free: 254408, Largest Avail: 144310, Total Aux: 738726, Largest Aux Avail: 4454
GL_MAX_SAMPLES_EXT: 4
Gtk-Message: Failed to load module "overlay-scrollbar"
CShaderDeviceMgrBase::GetRecommendedConfigurationInfo: CPU speed: 1999 MHz, Processor: GenuineIntel
GlobalMemoryStatus: 2027945984
CShaderDeviceMgrBase::GetRecommendedConfigurationInfo: CPU speed: 1999 MHz, Processor: GenuineIntel
GlobalMemoryStatus: 2027945984
[0215/180427:ERROR:resource_bundle.cc(411)] Failed to load /home/amk/.local/share/Steam/SteamApps/andrech/Team Fortress 2/cef_gtk.pak
Some features may not be available.
[0215/180427:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
IDirect3DDevice9::Create: BackBufWidth: 1920, BackBufHeight: 1080, D3DFMT: 3, BackBufCount: 1, MultisampleType: 0, MultisampleQuality: 0
/home/amk/.local/share/Steam/SteamApps/andrech/Team Fortress 2/hl2.sh: line 72:  5588 Segmentation fault      (core dumped) ${GAME_DEBUGGER} "${GAMEROOT}"/${GAMEEXE} "$@"
Game removed: AppID 440 "Team Fortress 2", ProcID 5588 
Generating new string page texture 116: 256x256, total string texture memory is 3.03 MB
saving roaming config store to 'sharedconfig.vdf'
roaming config store 2 saved successfully
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
Generating new string page texture 118: 8x256, total string texture memory is 3.04 MB
Generating new string page texture 120: 512x256, total string texture memory is 3.56 MB
CAPIJobRequestUserStats - Server response failed 2

---

### Post by Perfect Storm on 2013-02-15
Have you read and install  this: [https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics](https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics)

---

