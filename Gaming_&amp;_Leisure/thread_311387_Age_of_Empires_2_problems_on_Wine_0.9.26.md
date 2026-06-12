---
title: "Age of Empires 2 problems on Wine 0.9.26"
date: 2006-12-02
forum: Gaming &amp; Leisure
---

### Post by HandGrenade on 2006-12-02
It installed just fine, but I get this error. This is my first attempt at using Wine.

bob@bob-laptop:~$ wine ~/.wine/drive_c/Program\ Files/Microsoft\ Games/Age\ of\ Empires\ II/empires2.exe
Unknown device ID 3150, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
Unknown device ID 3150, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
wine: Unhandled page fault on read access to 0xffffffff at address 0x40aa66 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x0040aa66).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0040aa66 ESP:0033fd98 EBP:0033fe7c EFLAGS:00010216(   - 00      -RIAP1)
 EAX:0033fd9c EBX:00000001 ECX:00000067 EDX:00400000
 ESI:7b8762e3 EDI:00400000
Stack dump:
0x0033fd98:  00410fed 00000000 00400000 00000067
0x0033fda8:  7ffdf000 00115b53 7b8a58a0 00450038
0x0033fdb8:  7bc762c4 00450000 00450f48 0033fde4
0x0033fdc8:  7bc36828 00000024 00000094 00000005
0x0033fdd8:  00000001 00000a28 00000002 76726553
0x0033fde8:  20656369 6b636150 7b003220 00000800
Backtrace:
=>1 0x0040aa66 in empires2 (+0xaa66) (0x0033fe7c)
  2 0x0041ace2 in empires2 (+0x1ace2) (0x0033ff08)
  3 0x7b86d49f in kernel32 (+0x4d49f) (0x0033ffe8)
  4 0xb7e683b7 wine_switch_to_stack+0x17 in libwine.so.1 (0x00000000)
0x0040aa66: iret
Modules:
Module  Address                 Debug info      Name (50 modules)
PE      400000-44b000   Export          empires2
PE      10000000-1000c000       Deferred        drvmgt
ELF     7b800000-7b917000       Export          kernel32<elf>
  \-PE  7b820000-7b917000       \               kernel32
ELF     7bc00000-7bc81000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc81000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7df14000-7df18000       Deferred        libxfixes.so.3
ELF     7df18000-7df21000       Deferred        libxcursor.so.1
ELF     7df21000-7df3d000       Deferred        imm32<elf>
  \-PE  7df30000-7df3d000       \               imm32
ELF     7df3d000-7df45000       Deferred        libxrender.so.1
ELF     7df45000-7df48000       Deferred        libxinerama.so.1
ELF     7e6a9000-7e893000       Deferred        r300_dri.so
ELF     7e893000-7e89a000       Deferred        libdrm.so.2
ELF     7e89a000-7e900000       Deferred        libgl.so.1
ELF     7e900000-7e9e6000       Deferred        libx11.so.6
ELF     7e9e6000-7e9f3000       Deferred        libxext.so.6
ELF     7e9f3000-7ea0b000       Deferred        libice.so.6
ELF     7ea0b000-7ea98000       Deferred        winex11<elf>
  \-PE  7ea20000-7ea98000       \               winex11
ELF     7ea98000-7eab7000       Deferred        libexpat.so.1
ELF     7eab7000-7eae5000       Deferred        libfontconfig.so.1
ELF     7eae5000-7eaf9000       Deferred        libz.so.1
ELF     7eaf9000-7eb62000       Deferred        libfreetype.so.6
ELF     7eb62000-7eb76000       Deferred        lz32<elf>
  \-PE  7eb70000-7eb76000       \               lz32
ELF     7eb76000-7eb8f000       Deferred        version<elf>
  \-PE  7eb80000-7eb8f000       \               version
ELF     7eb8f000-7ebd3000       Deferred        advapi32<elf>
  \-PE  7eba0000-7ebd3000       \               advapi32
ELF     7ebd3000-7ebdd000       Deferred        libgcc_s.so.1
ELF     7ebe0000-7ebe3000       Deferred        libxrandr.so.2
ELF     7ebe3000-7ebeb000       Deferred        libsm.so.6
ELF     7ecc0000-7ed74000       Deferred        gdi32<elf>
  \-PE  7ece0000-7ed74000       \               gdi32
ELF     7ed74000-7eea7000       Deferred        user32<elf>
  \-PE  7ed90000-7eea7000       \               user32
ELF     7efb1000-7efbb000       Deferred        libnss_files.so.2
ELF     7efbb000-7efd0000       Deferred        libnsl.so.1
ELF     7efd0000-7eff2000       Deferred        libm.so.6
ELF     7eff2000-7eff7000       Deferred        libxxf86vm.so.1
ELF     7eff7000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d04000-b7d0d000       Deferred        libnss_compat.so.2
ELF     b7d0e000-b7d11000       Deferred        libdl.so.2
ELF     b7d11000-b7e40000       Deferred        libc.so.6
ELF     b7e40000-b7e52000       Deferred        libpthread.so.0
ELF     b7e54000-b7e57000       Deferred        libxau.so.6
ELF     b7e61000-b7f72000       Export          libwine.so.1
ELF     b7f75000-b7f8b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Microsoft Games\Age of Empires II\empires2.exe
        00000009    0 <==

---

### Post by HandGrenade on 2006-12-02
I think it might be a driver problem, seeing as:

bob@bob-laptop:~$ glxinfo
name of display: :0.0
Unknown device ID 3150, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20040924 TCL
OpenGL version string: 1.2 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow


I have an ATI Mobility Radeon x600...

---

### Post by hikaricore on 2006-12-02
> **HandGrenade said:**
> I think it might be a driver problem


I'm going to have to say I don't believe it is..

> 
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135


^This says it's a missing file problem.  ntoskrnl.exe  to be more exact is probably missing, no clue what it's for just an observation.

Check the Wine Application DataBase when it's back online (I havn't been able to connect to the server tonight): [http://appdb.winehq.org/]("http://appdb.winehq.org/")

If there's any further information on your game you'll find it there.

Also if your program uses DirectX don't expect a wine to work very well with it.

---

### Post by HandGrenade on 2006-12-02
I checked the DB earlier and AOE2 had a Gold rating for Ubuntu. The only other thing it said the game needed was a crack, which I tried applying with negative results. However, I don't think that would contribute to a missing file...

---

### Post by hikaricore on 2006-12-03
One quick thought.

I see you were launching the game like this:
```
wine ~/.wine/drive_c/Program\ Files/Microsoft\ Games/Age\ of\ Empires\ II/empires2.exe
```

Do you have the same results while lanuching the game from it's directory rather than your home directory?

```

cd ~/.wine/drive_c/Program\ Files/Microsoft\ Games/Age\ of\ Empires\ II
wine empires2.exe

```

---

### Post by HandGrenade on 2006-12-03
When launching from the home directory I get this:

bob@bob-laptop:~$ cd ~/.wine/drive_c/Program\ Files/Microsoft\ Games/Age\ of\ Empires\ II
[email]bob@bob-laptop:~/.wine[/email]/drive_c/Program Files/Microsoft Games/Age of Empires II$ wine empires2.exe
Unknown device ID 3150, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
Unknown device ID 3150, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
wine: Unhandled page fault on read access to 0xffffffff at address 0x40aa66 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x0040aa66).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0040aa66 ESP:0033fd98 EBP:0033fe7c EFLAGS:00010216(   - 00      -RIAP1)
 EAX:0033fd9c EBX:00000001 ECX:00000067 EDX:00400000
 ESI:7b8762e3 EDI:00400000
Stack dump:
0x0033fd98:  00410fed 00000000 00400000 00000067
0x0033fda8:  7ffdf000 0011598c 7b8a58a0 00450038
0x0033fdb8:  7bc762c4 00450000 00450f98 0033fde4
0x0033fdc8:  7bc36828 00000024 00000094 00000005
0x0033fdd8:  00000001 00000a28 00000002 76726553
0x0033fde8:  20656369 6b636150 7b003220 00000800
Backtrace:
=>1 0x0040aa66 in empires2 (+0xaa66) (0x0033fe7c)
  2 0x0041ace2 in empires2 (+0x1ace2) (0x0033ff08)
  3 0x7b86d49f in kernel32 (+0x4d49f) (0x0033ffe8)
  4 0xb7de13b7 wine_switch_to_stack+0x17 in libwine.so.1 (0x00000000)
0x0040aa66: iret
Modules:
Module  Address                 Debug info      Name (50 modules)
PE      400000-44b000   Export          empires2
PE      10000000-1000c000       Deferred        drvmgt
ELF     7b800000-7b917000       Export          kernel32<elf>
  \-PE  7b820000-7b917000       \               kernel32
ELF     7bc00000-7bc81000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc81000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7df0f000-7df18000       Deferred        libxcursor.so.1
ELF     7df18000-7df34000       Deferred        imm32<elf>
  \-PE  7df20000-7df34000       \               imm32
ELF     7df34000-7df3c000       Deferred        libxrender.so.1
ELF     7df3c000-7df3f000       Deferred        libxinerama.so.1
ELF     7e6a0000-7e88a000       Deferred        r300_dri.so
ELF     7e88a000-7e891000       Deferred        libdrm.so.2
ELF     7e891000-7e8f7000       Deferred        libgl.so.1
ELF     7e8f7000-7e9dd000       Deferred        libx11.so.6
ELF     7e9dd000-7e9ea000       Deferred        libxext.so.6
ELF     7e9ea000-7ea02000       Deferred        libice.so.6
ELF     7ea02000-7ea8f000       Deferred        winex11<elf>
  \-PE  7ea10000-7ea8f000       \               winex11
ELF     7ea8f000-7eaae000       Deferred        libexpat.so.1
ELF     7eaae000-7eadc000       Deferred        libfontconfig.so.1
ELF     7eadc000-7eaf0000       Deferred        libz.so.1
ELF     7eaf0000-7eb59000       Deferred        libfreetype.so.6
ELF     7eb59000-7eb6d000       Deferred        lz32<elf>
  \-PE  7eb60000-7eb6d000       \               lz32
ELF     7eb6d000-7eb86000       Deferred        version<elf>
  \-PE  7eb70000-7eb86000       \               version
ELF     7eb86000-7ebca000       Deferred        advapi32<elf>
  \-PE  7eb90000-7ebca000       \               advapi32
ELF     7ebca000-7ebd4000       Deferred        libgcc_s.so.1
ELF     7ebd6000-7ebda000       Deferred        libxfixes.so.3
ELF     7ebda000-7ebe2000       Deferred        libsm.so.6
ELF     7ecb7000-7ed6b000       Deferred        gdi32<elf>
  \-PE  7ecd0000-7ed6b000       \               gdi32
ELF     7ed6b000-7ee9e000       Deferred        user32<elf>
  \-PE  7ed90000-7ee9e000       \               user32
ELF     7efa8000-7efb2000       Deferred        libnss_files.so.2
ELF     7efb2000-7efbb000       Deferred        libnss_nis.so.2
ELF     7efbb000-7efd0000       Deferred        libnsl.so.1
ELF     7efd0000-7eff2000       Deferred        libm.so.6
ELF     7eff2000-7eff5000       Deferred        libxrandr.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c81000-b7c86000       Deferred        libxxf86vm.so.1
ELF     b7c87000-b7c8a000       Deferred        libdl.so.2
ELF     b7c8a000-b7db9000       Deferred        libc.so.6
ELF     b7db9000-b7dcb000       Deferred        libpthread.so.0
ELF     b7dcd000-b7dd0000       Deferred        libxau.so.6
ELF     b7dda000-b7eeb000       Export          libwine.so.1
ELF     b7eee000-b7f04000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Microsoft Games\Age of Empires II\empires2.exe
        00000009    0 <==

---

### Post by hikaricore on 2006-12-03
Hmm... I'm not entirely sure at this point, I do see that it may be video related with the mentions of your graphic driver.  There have been alot of problems with ATI cards and 3d games, so I don't know if there's much hope at this point.  Make sure you've got the correct video drivers installed for your card and make sure you aren't running beryl or compiz at the time you're launching the game (you'd know if you were lol no guessing to that one) other than that I don't know if I can be much help.

Good luck,

--Aaron

---

### Post by HandGrenade on 2006-12-03
Thanks for the help man.

I'm not really sure where to even start, I don't even know what driver I'm currently using. I've read about editing a certain file and changing 'ati' to 'radeon', or using fglrx or something similar. Does anyone have any suggestions? Apologies for my ignorance.

---

### Post by kvonb on 2006-12-03
ATIs are a nightmare at the best of times, the best thing to happen to them is Edgy where they (well mine at least) works perfectly out of the box!


First thing is to open a terminal and type this:

glxinfo | grep direct

If you get the answer "Yes", it means that you have direct rendering working so it most likely is a WINE/AoE2 problem, if "No", it's more likely a driver problem and you are going to have to install the proper driver for your card.

Do a search on the main Forum page for "ATI driver".  You will find lots of instruction pages but make sure you follow the guide for Dapper as I gather that's what you are running.

Or alternatively upgrade to Edgy, although that might be a whole other nightmare!

Try this, it might just persuade you to go to Edgy:

[http://ubuntuforums.org/showthread.php?t=301364](http://ubuntuforums.org/showthread.php?t=301364)

I've had AoE2 running under Cedega, although it was extremely slow and not much fun once you had more than a handful of units on the map.

Another thought: did you run winecfg before installing AoE?  I'm sure you did, but just in case that makes a difference.

---

### Post by HandGrenade on 2006-12-03
bob@bob-laptop:~$ glxinfo | grep direct
Unknown device ID 3150, please report. Assuming plain R300.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
direct rendering: Yes

And yeah, I ran winecfg before trying to run AOE2.

I've considered upgrading to Edgy, but I'm kinda hesitant to do so since I have no way of backing up my 30 or so gigs of music, documents, and photos.

Edit:
Also, I have no idea what Beryl is, or if I should consider using it :/ I went to the homepage and didn't really learn anything.

---

### Post by hikaricore on 2006-12-03
Sorry I wasn't saying you should or shouldn't be using beryl, it's just that with other software such as beryl running, you may have graphical problems.  Since you're not running it no need to worry about it affecting what you're currently trying to do.  :)

---

### Post by kvonb on 2006-12-03
Don't worry about all the Beryl/Compiz stuff right now, it's not your most pressing problem!

Try this:

```
lspci | grep Display
```And post the result

---

### Post by HandGrenade on 2006-12-03
bob@bob-laptop:~$ lspci | grep Display
bob@bob-laptop:~$

Nothing happened :(

---

### Post by kvonb on 2006-12-03
Maybe hikaricore is on the right track in that it's a WINE problem, have you looked through [http://www.winehq.com/](http://www.winehq.com/) ?

Also which version of WINE are you using and how did you install it?  That might be the difference.

If you can pay the $15US it costs to join, you could always try Cedega ([www.transgaming.com)](www.transgaming.com)), that will give you a 3 month subscription and you just cancel before the 3 months is up and you can continue to use Cedega, just not get new updates.  Plus you can ask them the hard questions :).

Regards, Kev :)

---

### Post by HandGrenade on 2006-12-03
I'm using 0.9.26, and installed it through Automatix2.

Also, I already pay for a WoW subscription, so I really can't afford to pay another monthly fee for Cedega :/

Thanks for the continued help, by the way :)

---

### Post by HandGrenade on 2006-12-03
By the way, The Wine App DB is up again, and the link to AOE2 is [http://appdb.winehq.org/appview.php?iVersionId=147]("http://appdb.winehq.org/appview.php?iVersionId=147")

---

