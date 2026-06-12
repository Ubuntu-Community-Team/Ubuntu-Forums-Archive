---
title: "Steam games quit right after launching"
date: 2014-02-14
forum: Gaming &amp; Leisure
---

### Post by amkxxx on 2014-02-14
Hi,
I've searched the forum but didn't find answer to my problem. When I try to launch any game in steam (tried Counter-Strike Source/1.6 Half-life 1&2) it shows "preparing to launch" window, then game loading screen shows for a blink of an eye, and I'm back to steam.
I'm using Ubuntu 13.10 x64 with bumblebee and nvidia 331 drivers. glxgears/spheres work just fine, steam doesn't report any errors when launched with optirun. This is output I get from terminal:

[FONT=courier new]amk@amk-notebook ~ $ optirun steam
Running Steam on linuxmint 16 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
unlinked 0 orphaned pipes
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0214/153021:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Generating new string page texture 2: 48x256, total string texture memory is 49,15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311,30 KB
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
Focused window is now 1, 0
Adding license for package 0
Adding license for package 1
Adding license for package 11
Adding license for package 164
Adding license for package 2294
Adding license for package 2621
Adding license for package 16222
Adding license for package 17250
Adding license for package 17427
Adding license for package 17634
Adding license for package 26346
Adding license for package 33317
Adding license for package 38716
Adding license for package 38717
roaming config store loaded successfully - 2695 bytes.
migrating temporary roaming config store
Installing breakpad exception handler for appid(steam)/version(1390852599_client)
ExecCommandLine: "/home/amk/.local/share/Steam/ubuntu12_32/steam"
System startup time: 8,48 seconds
OnFocusWindowChanged to window type: k_EWindowTypeSteamDesktop, 0
Generating new string page texture 72: 1024x256, total string texture memory is 1,36 MB
Generating new string page texture 73: 128x256, total string texture memory is 131,07 KB
Generating new string page texture 74: 128x256, total string texture memory is 1,49 MB
Generating new string page texture 75: 64x256, total string texture memory is 1,56 MB
Generating new string page texture 76: 32x256, total string texture memory is 1,59 MB

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
Generating new string page texture 79: 128x256, total string texture memory is 1,72 MB
Generating new string page texture 80: 512x256, total string texture memory is 2,24 MB
Generating new string page texture 81: 384x256, total string texture memory is 2,64 MB
Generating new string page texture 82: 24x256, total string texture memory is 2,66 MB
Generating new string page texture 83: 128x256, total string texture memory is 2,79 MB
Generating new string page texture 84: 8x256, total string texture memory is 2,80 MB
Running Steam on linuxmint 16 64-bit
STEAM_RUNTIME has been set by the user to: /home/amk/.local/share/Steam/ubuntu12_32/steam-runtime
ExecCommandLine: "/home/amk/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 101: 256x256, total string texture memory is 3,06 MB
Focused window is now 0, 0
OnFocusWindowChanged to window type: k_EWindowTypeNonSteamDesktop, 0
Focused window is now 1, 0
OnFocusWindowChanged to window type: k_EWindowTypeSteamDesktop, 0
Game update: AppID 240 "Counter-Strike: Source", ProcID 13961, IP 0.0.0.0:0
ERROR: ld.so: object '/home/amk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
CGameStreamThread: Added instance ID 13961 for appid 240
CGameStreamThread: Set render instance ID 13961 for appid 240
ERROR: ld.so: object '/home/amk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
CGameStreamThread: Added instance ID 13962 for appid 240
pid 13964 != 13963, skipping destruction (fork without exec?)
ERROR: ld.so: object '/home/amk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/home/amk/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
CGameStreamThread: Added instance ID 13963 for appid 240
CGameStreamThread: Added instance ID 13965 for appid 240
CGameStreamThread: Added instance ID 13966 for appid 240
SDL video target is 'x11'
SDL video target is 'x11'
CGameStreamThread: Set render instance ID 13966 for appid 240
Installing breakpad exception handler for appid(gameoverlayui)/version(20140125134503_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0214/153044:WARNING:proxy_service.cc(958)] PAC support disabled because there is no system implementation
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Using breakpad crash handler
Setting breakpad minidump AppID = 240
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561197970878275 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561197970878275
Did not detect any valid joysticks.
[0214/153047:ERROR:resource_bundle.cc(411)] Failed to load /home/amk/.local/share/Steam/SteamApps/common/Counter-Strike Source/cef_gtk.pak
Some features may not be available.
[0214/153048:WARNING:proxy_service.cc(646)] PAC support disabled because there is no system implementation
Focused window is now 0, 0
OnFocusWindowChanged to window type: k_EWindowTypeNonSteamDesktop, 0
This system supports the OpenGL extension GL_EXT_framebuffer_object.
This system supports the OpenGL extension GL_EXT_framebuffer_blit.
This system supports the OpenGL extension GL_EXT_framebuffer_multisample.
This system DOES NOT support the OpenGL extension GL_APPLE_fence.
This system supports the OpenGL extension GL_NV_fence.
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
This system supports the OpenGL extension GL_ARB_debug_output.
This system supports the OpenGL extension GL_EXT_direct_state_access.
This system supports the OpenGL extension GL_NV_bindless_texture.
This system DOES NOT support the OpenGL extension GL_AMD_pinned_memory.
This system supports the OpenGL extension GL_EXT_framebuffer_multisample_blit_scaled.
This system supports the OpenGL extension GL_EXT_texture_sRGB_decode.
This system supports the OpenGL extension GL_NVX_gpu_memory_info.
This system DOES NOT support the OpenGL extension GL_ATI_meminfo.
This system supports the OpenGL extension GL_EXT_texture_compression_s3tc.
This system supports the OpenGL extension GL_EXT_texture_compression_dxt1.
This system DOES NOT support the OpenGL extension GL_ANGLE_texture_compression_dxt3.
This system DOES NOT support the OpenGL extension GL_ANGLE_texture_compression_dxt5.
This system DOES NOT support the OpenGL extension GLX_EXT_swap_control_tear.
GL_NV_bindless_texture: DISABLED
GL_AMD_pinned_memory: DISABLED
GL_EXT_texture_sRGB_decode: AVAILABLE
GL_NVX_gpu_memory_info: AVAILABLE
GL_ATI_meminfo: UNAVAILABLE
GL_NVX_gpu_memory_info: Total Dedicated: 2097152, Total Avail: 2097152, Current Avail: 2056668
GL_MAX_SAMPLES_EXT: 32
CShaderDeviceMgrBase::GetRecommendedConfigurationInfo: CPU speed: 2501 MHz, Processor: GenuineIntel
GlobalMemoryStatus: 4042260480
CShaderDeviceMgrBase::GetRecommendedConfigurationInfo: CPU speed: 2501 MHz, Processor: GenuineIntel
GlobalMemoryStatus: 4042260480
IDirect3DDevice9::Create: BackBufWidth: 1920, BackBufHeight: 1080, D3DFMT: 3, BackBufCount: 1, MultisampleType: 0, MultisampleQuality: 0
GL sampler object usage: ENABLED
GL prefer MapBufferRange: NO

 ##### swap interval = 0     swap limit = 1 #####
The program 'hl2_linux' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 136 error_code 3 request_code 15 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
/home/amk/.local/share/Steam/SteamApps/common/Counter-Strike Source/hl2.sh: line 67: 13966 Segmentation fault      ${GAME_DEBUGGER} "${GAMEROOT}"/${GAMEEXE} "$@"
Game removed: AppID 240 "Counter-Strike: Source", ProcID 13966 
Focused window is now 1, 0
OnFocusWindowChanged to window type: k_EWindowTypeSteamDesktop, 0

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:13847): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.


Help me please I've been trying to get it work for a month!
[/FONT]

---

### Post by dannyboy79 on 2014-02-14
what does this return?
```
sudo lshw -C display
```
you need to get your drivers running correctly on your system first.

---

### Post by amkxxx on 2014-02-16
Hi thanks for replying. Here's terminal output:

[FONT=courier new]*-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:d3000000-d33fffff memory:e0000000-efffffff ioport:4000(size=64)[/FONT]

Does it mean that system only recognizes intel card?

Here's a tutorial for installing bumblebee and drivers that I used and followed step by step
[http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271](http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271)

---

### Post by dannyboy79 on 2014-02-17
i have no experience with bumblebee or dual graphics. from what it looks like, i don't see your nvidia gfx chip. are you sure it's enabled in the bios? did you receive any errors during the bumblebee install?

---

### Post by barbarah2 on 2014-02-24
I used to have an issue that looked a lot like yours and it turned out to be all about drivers

---

### Post by knpoe on 2014-02-24
video driver issue- fix / install different video drivers then fully reinstall steam... i would assume.
**ALSO assuming you've plugged your monitor into the nvidia output and not the onboard intel output..  .. 

331 nvidia drivers dont work well for me- im still on 319- with 13.10 from official nvidia site. they seem to be smoothest on my 560gtx idk why

so essentially the easiest fix- boot to single user mode easiest- or just kill your xserver from tty{1-5}
[B]remove any nvidia drivers you installed with apt-get
[/B]uninstall steam - - or at the very least delete your game files *- if you like to be thorough -* 
[B]get the 319 drivers
[/B]```
 wget http://us.download.nvidia.com/XFree86/Linux-x86_64/319.49/NVIDIA-Linux-x86_64-319.49.run 
```
[B]make em runable
[/B]```
 chmod +x ./NVIDIA-Linux-x86_64-319.49.run 
```
**run em, ***when prompted to install dkms kern modules, select the default No option -*```
 ./NVIDIA-Linux-x86_64-319.49.run 
```
**update and upgrade** packages
```
 apt-get update ; apt-get upgrade -y 
```
***rebooterize the system***
```
 init 6 
```
if any issues you may need to perform steps from here: [https://wiki.debian.org/NvidiaGraphicsDrivers](https://wiki.debian.org/NvidiaGraphicsDrivers) 

once your desktop and steam are all happy- try to rerun the games- test on a freshly installed game... then test on a previously(prior to grfx driver change) installed game..  :)

---

