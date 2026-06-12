---
title: "World of Warcraft with Intel X3000 (G965): segmentation fault"
date: 2007-08-05
forum: Gaming &amp; Leisure
---

### Post by pucko on 2007-08-05
Have anyone tried this?

I can install the game fine with wine 0.9.41 but when I try to run it I first get a black screen and then after a second or two I'm back with a segmentation fault.

I have no idea what's wrong (I've followed the instructions on most guides out there on the webb, but doesn't seem to help).

If I try to run it with directx it just locks up the computer instead.

#wine WoW.exe -opengl
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7ceb0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7ceb0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
Segmentation fault (core dumped)

---

### Post by hikaricore on 2007-08-05
Please tell as much about your system hardware as possible otherwise I don't even know where to start.

---

### Post by pucko on 2007-08-06
Oh, sorry about that.

I run Feisty with some additional packages from various sources. Mainly kde-packages and from feisty-proposed and such.

It's a ASUS P5B-V motherboard with Core 2 Duo (E4300). The P5B-V has an integrated videocard, which is an Intel X3000 (also known as G965).

---

### Post by TOXIC0 on 2007-09-05
I have exactly the same message trying to play wow !!!! even with Cedega, it doesn't work !!!

here the end of the message :
```
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
Segmentation fault (core dumped)
```

up please !

My hardware ?
 Core Quad Q6600
 Gigabyte GA-965-GM-S2 with integrated Intel X3000 Video
 Huge amount of DDR2

Edit :
I use a 22" wide screen, so I had to install and use 915resolution plugin. Here more informations :
```
toxic@ToXiC-Quad:~$ glxinfo |grep direct
direct rendering: Yes

```
```
toxic@ToXiC-Quad:~$ glxgears -info
GL_RENDERER   = Mesa DRI Intel(R) 965G 4.1.3002 x86/MMX/SSE2
GL_VERSION    = 1.4 Mesa 6.5.2
GL_VENDOR     = Tungsten Graphics, Inc
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
44361 frames in 5.0 seconds = 8871.418 FPS
7909 frames in 5.0 seconds = 1581.778 FPS
7977 frames in 5.0 seconds = 1595.272 FPS
7954 frames in 5.0 seconds = 1590.726 FPS
7995 frames in 5.0 seconds = 1598.946 FPS

```
Note : The firs score :8871 make me think that perhaps, not the video card, but the CPU is working on graphics ! Something like that already hapened to me with an ATI X700... The processor Charge whyle glxgears is running is 5 to 22 % !! but on a quad-core, what does-it mean ? lol, usually, doing nothing on th PC uses between 0 an 5 %...max 11%.

Here my xorg.conf :
```

toxic@ToXiC-Quad:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "oss"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82G965 Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "LE2262"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82G965 Integrated Graphics Controller"
        Monitor         "LE2262"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Thats all I think, please, help me on that !!!!!



Edit 2 : Whith Cedega, I got the message :
```

WoW couldn't launch the 3D acceleration. Please insure DirectX 9.0c is installed and that your graphic drivers are up to date.

```
PS. : sorry for the bad translation, I'm french

And in cedega, when i start WoW with the "-opengl" parameter, it starts a black screen, and nothing, not even able to get back to ubuntu ! I started it windowed, the window is black, and the mouse stuck in a virtual black square in the window. no way to get back to ubuntu.

I just want to say, I tryed a fresh install from the CD's, (with the wtf directory empty !!!) AND my windows install (with AND without addons)... nothing works !!!

Now i'm pretty sure it comes from the integrated Intel graphic card.


Edit 3 : I also addes many things to "speedup" wow in the registery, tryed some .reg registery fixing patches, nothing works ! Not with wine, and not with Cedega (the full version, v5.2.3).


Last Edit : 
Here the exact output when I start WoW whith wine :
```

toxic@ToXiC-Quad:~$ wine /media/DATA/wow_linux/World\ of\ Warcraft/WoW.exe 
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7bf20000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7bf20000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed40,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33f74c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x137088) : stub, simulating 64MB for now, returning 64MB left
Erreur de segmentation (core dumped)
toxic@ToXiC-Quad:~$ 

```

Thanks for the help .....

---

### Post by zyth on 2007-09-07
You may wish to browse this thread - 

[http://ubuntuforums.org/showthread.php?t=496876&highlight=intel+wine+warcraft](http://ubuntuforums.org/showthread.php?t=496876&highlight=intel+wine+warcraft)

However, there seems to be no solution for this issue at this point.

---

