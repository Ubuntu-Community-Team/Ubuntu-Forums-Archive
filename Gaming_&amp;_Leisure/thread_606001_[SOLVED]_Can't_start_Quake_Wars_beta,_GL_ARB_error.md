---
title: "[SOLVED] Can't start Quake Wars beta, GL_ARB error."
date: 2007-11-07
forum: Gaming &amp; Leisure
---

### Post by Programmerer on 2007-11-07
Hello, I have installed ETQW, but I can't start it, because it says that my graphics card don't support some kind of shading.
Other games, such as ET and ActionCube works without any problems.
  I have a nVidia GeForce4 Ti 4200 card, and I installed the driver for nVidia from Restricted Drivers Manager, but I have also downloaded a driver for Linux, NVIDIA-Linux-x86-96.43.01-pkg1.run, but I can't install it, because it says that I can't run it with a X server, and I have tried to install it from the terminal when you click Ctrl+Alt+F1, but the same problem appeared there to.

Here is the error from ETQW:
> ...loading binary 'generated/declb/localization/locstr/maps/slipgate.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/valley.locstrb'
...loading binary 'generated/declb/localization/locstr/maps/volcano.locstrb'
------------------------------
couldn't exec 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
couldn't exec 'etqwbinds.cfg'
execing 'autoexec.cfg'
TODO: Sys_GetGfxDeviceIdentification
Vendor: Device:
/proc/cpuinfo CPU frequency: 1700.17 MHz
parse /proc/cpuinfo for CPU information
parse had a problem
detecting video ram (set sys_videoRam on command line to override) ..
found XNVCtrl extension 1.12
Detected
        1 1.70 GHz CPU
        496 MB of System memory
        64 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1280x1024
execing 'specs/minspec.dat'
execing 'specs/minspec_cpu.dat'
execing 'specs/minspec_gamedetail.dat'
execing 'specs/minspec_gpu.dat'
execing 'specs/minspec_gpudetail.dat'
execing 'specs/minspec_lighting.dat'
execing 'specs/minspec_foliage.dat'
TODO: Sys_GetGfxDeviceIdentification
Vendor: Device:
execing 'specs/recspec_foliage.dat'
Opening IP socket: localhost:-1
SDL_ListModes:
1600x1024 1280x1024 1440x900 1280x1024 1280x960 1280x800 1280x768 1152x864 1152x768 1024x768 840x525 
832x624 800x600 800x512 720x450 720x400 640x512 640x480 640x400 640x384 640x350 
576x432 576x384 512x384 416x312 400x300 360x200 320x240 320x200 320x175 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
thread priority set to 1
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 8.000000
...using GL_1.4_texture_lod_bias
...using GL_EXT_shared_texture_palette
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
X..GL_EXT_texture_rectangle not found
...using GL_EXT_stencil_wrap
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
X..GL_ARB_fragment_program not found
X..GL_EXT_depth_bounds_test not found
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
X..GL_EXT_framebuffer_object not found
X..GL_EXT_packed_depth_stencil not found
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
...using GL_ARB_shader_objects
...using GL_ARB_vertex_shader
X..GL_ARB_fragment_shader not found
X..GL_ARB_fragment_program_shadow not found
...using GL_ARB_shadow
...using GL_ARB_depth_texture
...using GL_EXT_gpu_program_parameters
0x0
[0x082cc6d1]
[0x08192769]
[0x08101078]
[0x08101ad9]
[0x0819085c]
[0x08190e02]
[0x08190fde]
[0x083ee00e]
[0xb7b34050]
[0x0804c9d1]
********************
ERROR: The current video card / driver combination does not support the necessary features: GL_ARB_fragment_program GL_ARB_fragment_shader
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
Sys_Error: Error during initialization


---

### Post by FG123 on 2007-11-07
Couple of things:

(a) You're attempting to install driver version 43.01 by hand, while Ubuntu can automatically install and setup the latest driver (96.39 for your card I believe). So yeah, you're attempting to install a driver that's SOOOOOO out of date it's not funny.

So, click System -> Administration -> Restricted Drivers Manager, click the checkbox next to your card which should be listed there, and follow the instructions.

(b) Even with the latest drivers I'm not convined the game will run. You say games such as ET and ActionCube work without any problems, but you're forgetting these games are either old and/or running on simpler engines. Quake Wars is about a month old, running on an extremely advanced version of the Doom 3 engine. It's damn powerful, which may need more than your card can supply.

---

