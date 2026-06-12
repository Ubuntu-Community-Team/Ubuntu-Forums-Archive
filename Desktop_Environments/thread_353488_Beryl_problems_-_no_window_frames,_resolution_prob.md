---
title: "Beryl problems - no window frames, resolution problems and blank Terminal"
date: 2007-02-04
forum: Desktop Environments
---

### Post by Skuldi on 2007-02-04
So, I have ubuntu and installed Beryl recently. Now it works fine... almost. I have no window frames and if I open the Terminal, I can't see anything, it's just white.
Also if I try to change the resolution to anything higher than 1024 with NVIDIA X Server Settings (I have a 7900GS), my screen gets pretty messed up and the system crashes. It's hard to describe how it looks... basically, it's at the higher resolution, but my former screen is on 1024 in the upper left corner and the right and bottom corners are white - can't take a screenshot as it crashes.
These errors only occur, if I have the Beryl Windows Manager activated, though.

See screenshots for the blank Terminal and missing window frames:

[Without Beryl](http://i10.photobucket.com/albums/a103/SkuldOMG/Bildschirmfoto.png)

[With Beryl](http://i10.photobucket.com/albums/a103/SkuldOMG/Bildschirmfoto-1.png)

---

### Post by Skuldi on 2007-02-05
Okay I got rid of the missing window frames and blank console problem - still I have the problem that it looks very weird when I  have a resolution higher than 1024 - see [this screenshot](http://i10.photobucket.com/albums/a103/SkuldOMG/Bildschirmfoto-2.png).

---

### Post by anuradha.d on 2007-02-05
hey pal,

i'm also using beryl with emerald themes in my compaq presario v3000. but with an intel Mobile 945GM/GMS/940GML Express Integrated Graphics Controller. everything works fine. one suggestion, in the advanced beryl options select 'force Nvidia' as the rendering platform. this might help you to run beryl smoothly with Nvidia. not 100% sure though. 

good luck

---

### Post by Skuldi on 2007-02-05
Hm, I can't seem to find advanced options, where is it located?

---

### Post by shareMenaPeace on 2007-02-05
Which nvidia driver you use? (official or unofficial).

What happens if you type in console

```
glxinfo
```

(should output glx is enabled along other stuff).

How looks your  /etc/X11/xorg.conf ? On the bottom of the file is the Section "Screen", check here what resolution you can display. If there is a 32 depth or 16 depth value change it to 24. 
Does the Sectiion "Device" looks similar to this?
> Section "Device"
	Identifier     "NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev" "true"
	Option		"RenderAccel" "true"
	Option		"AllowGLXWithComposite" "true"
	Option		"backingstore" "true"
	Option		"AddARGBGLXVisuals" "True"
	Option		"TripleBuffer" "true"
EndSection
If there is "nv" change it to "nvidia"

PCI can be found by checking 

> lspci


And which guide you used (link?)

---

### Post by Skuldi on 2007-02-05
on "glxinfo" I get:

> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7900 GS/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.0 NVIDIA 97.46
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

And after that a long table.

My xorg.conf Device:

> Section "Device"
    Identifier     "NVIDIA GeForce 7800GS"
    Driver         "nvidia"
Option "TripleBuffer" "true"
EndSection

In the Screen section, do you mean the default depth? It's at 24.

This is what it shows on entering lspci:

> 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0292 (rev a1)


---

### Post by thk on 2007-02-05
> **Skuldi said:**
> Okay I got rid of the missing window frames and blank console problem - still I have the problem that it looks very weird when I  have a resolution higher than 1024 - see [this screenshot](http://i10.photobucket.com/albums/a103/SkuldOMG/Bildschirmfoto-2.png).
I have exactly the same problem. What was your fix?

---

### Post by Skuldi on 2007-02-05
> **thk said:**
> I have exactly the same problem. What was your fix?


[This thread](http://ubuntuforums.org/showthread.php?t=352088).

> * Add this to xorg.conf "Screen" section

# Enable 32-bit ARGB GLX Visuals
Option "AddARGBGLXVisuals" "True"

&

* Add this to xorg.conf "Device" section

Option "TripleBuffer" "true"

. The result. Themes change. Min Max buttons present and terminals render correctly instead of white!!! 

---

### Post by rrpnow on 2007-02-06
i tried the fixes above, but im still running the same problem... any other fixes>

---

### Post by shareMenaPeace on 2007-02-06
Well you can try reinstall (This goes pretty fast). 
I did that today and some small things changed (nothing bad so far) actualy it runs more stable.
[http://ubuntuforums.org/showthread.php?t=354228](http://ubuntuforums.org/showthread.php?t=354228)

---

### Post by shareMenaPeace on 2007-02-06
Skuldi i have the same nvidia "unknown" device you might try to add the pci bus to the xorg.conf 

(Please be aware im a noob  and this can lead to a none booting ubuntu (user account).
You can fix this than of course with recovery mode and edit xorg.conf with

```
nano -B /etc/X11/xorg.conf
```

Try this for device... maybe wait for more help but i think this works.. maybe you could still reinstall for better performance.

```

Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card"
Driver "nvidia"
BusID "PCI:5:0:0"
Option "UseFBDev" "true"
Option "RenderAccel" "true"
Option "AllowGLXWithComposite" "true"
Option "backingstore" "true"
Option "AddARGBGLXVisuals" "True"
Option "TripleBuffer" "true"
EndSection
```

---

### Post by Skuldi on 2007-02-06
Ok, the reinstall didn't fix the resolution problem ;)

EDIT: Neither did the changing of the xorg.conf fix it - I couldn't boot and put the Device back to 

> Identifier "NVIDIA GeForce 7800GS"
Driver "nvidia"
Option "TripleBuffer" "true"

---

### Post by thk on 2007-02-06
Thanks. That did the trick. (I added a few additional device options after searching other threads.)

---

### Post by rrpnow on 2007-02-06
can you post up the additional stuff you added? because i tried the above and it didn't work...

thanks

---

### Post by thk on 2007-02-06
> **rrpnow said:**
> can you post up the additional stuff you added? because i tried the above and it didn't work...

thanks

```

    Option         "AllowGLXWithComposite" "true"
    Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
    Option         "AddARGBGLXVisuals" "True"

```

This worked for me except for some blacked out windows. I'm told that can be fixed by turning off blur effects. I've not yet tried it. YMMV.

---

### Post by shareMenaPeace on 2007-02-06
> **rrpnow said:**
> can you post up the additional stuff you added? because i tried the above and it didn't work...

thanks

Open a terminal and type

```
lspci
```
Post teh output here or check yourself which PCI SLOT your grafic card is at - Looks liek something like 04:00:00. In this example the above code should than be 

```
BusID "PCI:4:0:0"
```

But well i dont know what effects the enabled features has if your grafics no support it.
Maybe someone else can point this out ?

Cheers

---

### Post by rrpnow on 2007-02-06
> **shareMenaPeace said:**
> Open a terminal and type

```
lspci
```
Post teh output here or check yourself which PCI SLOT your grafic card is at - Looks liek something like 04:00:00. In this example the above code should than be 

```
BusID "PCI:4:0:0"
```

But well i dont know what effects the enabled features has if your grafics no support it.
Maybe someone else can point this out ?

Cheers


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)


im going to assume its 01:00.0

but would i put PCI:01:00.0 or PCI:1:0:0 ...

---

### Post by shareMenaPeace on 2007-02-06
It is
> BusID "PCI:1:0:0"

Btw LOL do you got a dell620?

Cheers

---

### Post by rrpnow on 2007-02-06
> **shareMenaPeace said:**
> 
Btw LOL do you got a dell620?


yea... you?

---

### Post by shareMenaPeace on 2007-02-06
Yes same :)
So did this worked? Andy please post your xorg.conf too as my screen resolution is fine but i wonder as i just have a few modes.

my xorg.conf -- it is not perfect yet! 
```
Section "Device"
	Identifier     "NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev" "true"
	Option		"RenderAccel" "true"
	Option		"AllowGLXWithComposite" "true"
	Option		"backingstore" "true"
	Option		"AddARGBGLXVisuals" "True"
	Option		"TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

```

---

### Post by rrpnow on 2007-02-06
nope... same problem... this time i wnet back to KDE, and my taskbar was blacked out, so i had to restart x

---

### Post by shareMenaPeace on 2007-02-06
Can you post your xorg.conf fiel please?

---

### Post by alphanerd on 2007-02-06
I had the exact same problem and tried lots of suggestions. Anyway the latest svn fixes this.
do this:

add the repo below and key then 

deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn
wget [http://3v1n0.tuxfamily.org/DD800CD9.gpg](http://3v1n0.tuxfamily.org/DD800CD9.gpg) -O- | sudo apt-key add -

sudo apt-get update
sudo apt-get dist-upgrade.

Works a treat!!!

---

### Post by rrpnow on 2007-02-06
> **shareMenaPeace said:**
> Can you post your xorg.conf fiel please?


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option	   "Maxtaptime" "0"
    Option	   "MinSpeed" "0.60"
    Option	   "MaxSpeed" "1.10"
    Option	   "AccelFactor" "0.030"
    Option	   "EdgeMotionMinSpeed" "200"
    Option	   "EdgeMotionMaxSpeed" "200"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    Option	   "UseFBDev" "true"
    Option	   "RenderAccel" "true"
    Option	   "AllowGLXWithComposite" "true"
    Option	   "backingstore" "true"
    Option         "AddARGBGLXVisuals" "True"
    Option	   "TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

---

### Post by mac.ryan on 2007-02-06
Hello guys... I'm having the same troubles here with my freshly arrived DELL M1710 (nVidia 9750 GTX(: the frame and top bar of windows are invisible when I try to use Beryl as windows manager...

I tried all the different bits you suggested in this thread (all the possible add-ons to the xorg.conf file, plus the update to the latest version of Beryl (but apt-get told me that I didn't need it).

Any further suggestion?

The only bit I found myself is that when i command-line "beryl" the output I get on the console stalls (meaning that the program stops outputting but the prompt doesn't come back) at the beryl system compatibility check:

> 
**************************************************************
* Beryl system compatiblity check                             *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32


I suspect that it might be something with the "depth 32", but even manually inserting it manually in the xorg.conf didn't help. Here below my xorg.conf (after I reverted to initial "freshly installed beryl" status) and pcilist output. Many thanks to those who will try to help! :)

> 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option 	   "TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection

    # Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

EndSection


lspci output:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0297 (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


---

### Post by shareMenaPeace on 2007-02-06
Thanks rppnow, and try this settings here
[HTML]Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card"
Driver "nvidia"
BusID "PCI:1:0:0"
#Option "UseFBDev" "true"
Option "RenderAccel" "true"
Option "AllowGLXWithComposite" "true"
Option "backingstore" "true"
Option "AddARGBGLXVisuals" "True"
Option "TripleBuffer" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device         "NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection
[/HTML]

---

### Post by rrpnow on 2007-02-07
yea, i tried that, but it didn't work... any other ideas!?!

---

### Post by shareMenaPeace on 2007-02-07
What happens if you start beryl from terminal? (Output message?)
[HTML]
beryl-manager[/HTML]

Check your xorg log file for "EE" or "WW" beginning lines to see if you haved errors.
```

gedit /var/log/Xorg.0.log
```

or post the file here ... 

Which beryl guide you used?
Do you installed NVIDIA drivers?


Well i had NVIDIA drivers running (used automatix to install "nvidia-settings") but yesterday i checked my xorg and noticed the few resolution modes. So i uninstalled and reinstalled the nvidia drivers with "envy".
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 
Before you try this i recommend to use this tool to automatic install nvidia driver 
[http://getautomatix.com](http://getautomatix.com) to install nvidia drivers - works.

I cant recommend "envy" actually ...as i had quiet some problems during this (Had no free disc space and no ubuntu cd during the install ... my fault but lead to wired login problems but sure try this if you have the cd and space.).

That lead to reconfigure me the xserver - well as you saw my xorg has now the modes but actually the resolution will not work....so still not complete xorg.conf -- but before and after BERYL and NVIDIA all the time works (with the right xorg.conf)it worked. Rightnow it runs pretty smooth.

---

### Post by rrpnow on 2007-02-07
> **shareMenaPeace said:**
> What happens if you start beryl from terminal? (Output message?)
[HTML]
beryl-manager[/HTML]

Check your xorg log file for "EE" or "WW" beginning lines to see if you haved errors.
```

gedit /var/log/Xorg.0.log
```

or post the file here ... 

Which beryl guide you used?
Do you installed NVIDIA drivers?


Well i had NVIDIA drivers running (used automatix to install "nvidia-settings") but yesterday i checked my xorg and noticed the few resolution modes. So i uninstalled and reinstalled the nvidia drivers with "envy".
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 
Before you try this i recommend to use this tool to automatic install nvidia driver 
[http://getautomatix.com](http://getautomatix.com) to install nvidia drivers - works.

I cant recommend "envy" actually ...as i had quiet some problems during this (Had no free disc space and no ubuntu cd during the install ... my fault but lead to wired login problems but sure try this if you have the cd and space.).

That lead to reconfigure me the xserver - well as you saw my xorg has now the modes but actually the resolution will not work....so still not complete xorg.conf -- but before and after BERYL and NVIDIA all the time works (with the right xorg.conf)it worked. Rightnow it runs pretty smooth.


here is my log...


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux linux 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb  7 14:51:40 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1028,01c2 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1028,01c2 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01c2 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01c2 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01c2 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01c2 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01c2 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1028,01c2 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1028,01c2 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01c2 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d7 card 1028,01c2 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:01:0: chip 1217,6972 card 2001,0000 rev 40 class 06,07,00 hdr 02
(II) PCI: 09:00:0: chip 14e4,1600 card 1028,01c2 rev 02 class 02,00,00 hdr 00
(II) PCI: 0c:00:0: chip 14e4,4311 card 1028,0007 rev 01 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,12), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdfefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:1), (0,12,12), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xdcf00000 - 0xdcffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 9: bridge is at (0:28:2), (0,9,9), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 9 non-prefetchable memory range:
	[0] -1	0	0xdce00000 - 0xdcefffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,7), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x52000000 - 0x54ffffff (0x3000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:1:0), (3,4,7), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x52000000 - 0x53ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x01d7) rev 161, Mem @ 0xdd000000/24, 0xc0000000/28, 0xde000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[1] -1	0	0xdcef0000 - 0xdcefffff (0x10000) MX[B]
	[2] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[3] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[4] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[7] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[8] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[9] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[10] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[11] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[14] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[15] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[16] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[1] -1	0	0xdcef0000 - 0xdcefffff (0x10000) MX[B]
	[2] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[3] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[4] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[5] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[6] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[7] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[8] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[9] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[10] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[11] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[14] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[15] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[16] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[5] -1	0	0xdcef0000 - 0xdcefffff (0x10000) MX[B]
	[6] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[7] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[14] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[20] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[21] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[22] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 09:56:41 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[5] -1	0	0xdcef0000 - 0xdcefffff (0x10000) MX[B]
	[6] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[7] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[14] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[20] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[21] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[22] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[5] -1	0	0xdcef0000 - 0xdcefffff (0x10000) MX[B]
	[6] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[7] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[17] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[23] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[24] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[25] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "TripleBuffer" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU Quadro NVS 110M at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.21.fc
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro NVS 110M at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (121, 120); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdcffc000 - 0xdcffffff (0x4000) MX[B]
	[8] -1	0	0xdcef0000 - 0xdcefffff (0x10000) MX[B]
	[9] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[10] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[11] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[20] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[26] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[27] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[28] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1440x900"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(**) NVIDIA(0): Option "BackingStore" "true"
(**) NVIDIA(0): Backing store enabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Setting defaults to alps values
(**) Option "MaxTapTime" "0"
(**) Option "HorizScrollDelta" "0"
(**) Option "EdgeMotionMinSpeed" "200"
(**) Option "EdgeMotionMaxSpeed" "200"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

---

### Post by shareMenaPeace on 2007-02-07
Ok
First off we have 2 diffrent D620 version 

You got the 1440x900 and me the 1280x800
To understand it better check out this Dell 620 Topic
[http://ubuntuforums.org/showthread.php?t=160679&highlight=dell+620+xorg](http://ubuntuforums.org/showthread.php?t=160679&highlight=dell+620+xorg)

I noticed your module xorg.conf section not loads the same stuff as i do add the below option to your Module in - and add also on bottom of xorg.conf the DRI part.

/etc/X11/xorg.conf
```
Section "Module"
	Load	"dri"
EndSection

Section "Device"
Option "DRI" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Than boot and try again but start beryl from terminal and see if there are any error messages.
Maybe you need to reconfigure the xsever. Checkout the ENVY script if it still not works . Uninstall NVIDIA than INSTALL again.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And read the first link ( i do this now too :) 100 post ... )

Cheers

---

### Post by shareMenaPeace on 2007-02-07
And change the Screen section aswell

```
Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NVIDIA Default Card"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900"
EndSubSection
EndSection
```

---

### Post by fmaste on 2007-02-07
I solved the problem of the window frames and blank Terminal by changing the DefaultDepth to 24 in the screen section of the xorg.conf.
Also add this to options
 Option "AddARGBGLXVisuals" "True"
 Option "TripleBuffer" "true"
to the device section

---

### Post by shareMenaPeace on 2007-02-08
Added DRI true to Device in xorg.conf dell 620 
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card"
Driver "nvidia"
BusID "PCI:1:0:0"
#Option "UseFBDev" "true"
Option "RenderAccel" "true"
Option "AllowGLXWithComposite" "true"
Option "backingstore" "true"
Option "AddARGBGLXVisuals" "True"
Option "TripleBuffer" "true"
Option "DRI" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device         "NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by lukanium on 2007-02-08
> **fmaste said:**
> I solved the problem of the window frames and blank Terminal by changing the DefaultDepth to 24 in the screen section of the xorg.conf.
Also add this to options
 Option "AddARGBGLXVisuals" "True"
 Option "TripleBuffer" "true"
to the device section

Thx man, this works .... :guitar: ...i do enjoy Beryl now :D

---

### Post by rrpnow on 2007-02-08
Hahahha! Nice It Works Now!! Thanks A Ton!!!

---

### Post by mac.ryan on 2007-02-08
> **fmaste said:**
> I solved the problem of the window frames and blank Terminal by changing the DefaultDepth to 24 in the screen section of the xorg.conf.
Also add this to options
 Option "AddARGBGLXVisuals" "True"
 Option "TripleBuffer" "true"
to the device section

You are a genius... it works like a charm now!

The problem was that I followed the instructions in the post of Skuldi (page 1) and he/she was saying to add the ARGBGLX option in teh Screen section, not in the device one...

Beautiful, thanks a zillion!! :)

---

### Post by piemur24 on 2007-02-13
How did you get the window frames back or fix the console?

---

### Post by Strider42 on 2007-02-13
Hi,

I have followed this thread religiously and still couldn't get Beryl to run correctly.  So today, I re-installed 6.10 and have applied all the updates.  I returned to the Beryl install in the UDSF and followed that with errors.  Still no luck.  I again followed this thread and have had rather more success.  Now the top bar displays with buttons and my terminal window is displaying correctly, but application and browser windows are black.  So is the desktop - all icons disappear.  Switching back to Metacity displays all windows and desktop correctly.  I'm hoping someone can come to the rescue as I'm sure it's probably a simple setting incorrectly applied - but I'm bashing my head against a wall now.  Below I have posted the outputs from glxinfo, lspci and my xorg.conf file in that order.

So if some kind soul can help me get Beryl working correctly I'll be very grateful.

Thanks
Paul


GLXINFO

paul@paul-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX Go5200/AGP/SSE2
OpenGL version string: 2.1.0 NVIDIA 97.46
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess


LSPCI

paul@paul-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


XORG.CONF

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dri"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Driver         "nvidia"
    BusID "PCI:1:0:0"
    Option "UseFBDev" "true"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Option "AddARGBGLXVisuals" "True"
    Option "backingstore" "true"
    Option "TripleBuffer" "true"
    Option "DRI"  "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by too_sick_for_you on 2007-02-13
I had the same problem.
Fixed it by modifying my xorg.conf file.
Areas I changed are notated in red.

```
Section "Device"
	Identifier	"NVIDIA GFORCE 7900 GT"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
      #Option		"UseFBDev"		"true" [COLOR="Red"]	DISABLED THIS[/COLOR] 
	Option "RenderAccel" "True" [COLOR="Red"]# ADDED THIS[/COLOR]
	Option "AllowGLXWithComposite" "true" [COLOR="Red"]# ADDED THIS[/COLOR]
	Option "TripleBuffer" "true" [COLOR="Red"]# ADDED THIS[/COLOR]
	Option "AddARGBGLXVisuals" "True" [COLOR="Red"]# ADDED THIS[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"	
	HorizSync	57.6-82
	VertRefresh	60-77
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GFORCE 7900 GT"
	Monitor		"Generic Monitor"
	DefaultDepth	24 [COLOR="Red"]# ADDED THIS[/COLOR]
	Option "TripleBuffer" "true" [COLOR="Red"]# ADDED THIS[/COLOR]
	Option "AllowGLXWithComposite" "True" [COLOR="Red"]# ADDED THIS[/COLOR]
	Option "RenderAccel" "True" [COLOR="Red"]# ADDED THIS[/COLOR]
	Option "AddARGBGLXVisuals" "True" [COLOR="Red"]# ADDED THIS[/COLOR]

	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Extensions" [COLOR="Red"]# ADDED THIS[/COLOR]
	Option "Composite" "Enable" [COLOR="Red"]# ADDED THIS[/COLOR]
EndSection [COLOR="Red"]# ADDED THIS[/COLOR]

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Strider42 on 2007-02-13
I have all those settings applied.  I have commented out UseFBDev, but still get the problem of black windows.

But this is I think definitely a screen resolution problem.  I have set my screen res to 1024 x 768 and it all works beautifully (well functionality wise).  But it looks awful on a Dell laptop screen that runs at 1920 x 1200.  So if anyone has any ideas on how to get this to work at higher resolutions I'd be grateful.

Thanks

Paul

---

### Post by hardawayd on 2007-02-13
> **Skuldi said:**
> Okay I got rid of the missing window frames and blank console problem - still I have the problem that it looks very weird when I  have a resolution higher than 1024 - see [this screenshot](http://i10.photobucket.com/albums/a103/SkuldOMG/Bildschirmfoto-2.png).

How did you get rid of the mission window frames?

---

### Post by GQed76 on 2007-02-13
these changes fixed my missing buttons, but the performance seems worse.

---

### Post by dracomordag on 2007-02-14
alright, i have problems...

[http://stashbox.org/12101/DSCF0051.JPG](http://stashbox.org/12101/DSCF0051.JPG) is as far as it gets, then it logs me out
[http://www.pastebin.ca/355978](http://www.pastebin.ca/355978) is my xorg.conf
[http://www.pastebin.ca/355979](http://www.pastebin.ca/355979) is my Xorg.0.log



help please?

---

### Post by Nacker123 on 2007-02-17
You might want to try changing the default resolution to 24 under "screen" section.

-Nacker
[http://eces.colorado.edu/~kaje/index.html](http://eces.colorado.edu/~kaje/index.html)

---

### Post by mawdryn on 2007-02-20
I've got two screens and have always had this problem with my second screen. After updating beryl last night, it happened to my primary screen.

Adding the following lines (in red)  to my xorg.conf fixed it for me.

```

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:1:0:0"
    Screen          0
[COLOR="Red"]    Option         "UseFBDev" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "backingstore" "true"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "true"[/COLOR]
EndSection

```

Don't have a clue if any one line was the key or what :confused:

.... grumble... still can't get the secondary to work, even though both sets of screen and device are practically identical...:confused:   I can live with that though, screen 1 isn't used anywhere near as much as screen 0.

BTW, Only been on Ubuntu for three weeks, and it Rocks \\:D/ 

------------------------------------
P4 3.2Ghz, 512Mb Ram,
256Mb GeForce 7300GT
And no Microsoft product within kooee distance :biggrin:

---

### Post by dracomordag on 2007-02-20
> **Nacker123 said:**
> You might want to try changing the default resolution to 24 under "screen" section.

-Nacker
[http://eces.colorado.edu/~kaje/index.html](http://eces.colorado.edu/~kaje/index.html)
i see no resolution-defining code sections

if you mean depth, youll notice it already is at 24

---

### Post by Skuldi on 2007-03-01
I still have the resolution problem, the screen is still messy if I try a resolution over 1024x768. I have tried every tip in this thread, I don't know how to solve it :/ :confused:

---

