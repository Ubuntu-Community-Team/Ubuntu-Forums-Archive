---
title: "Need some help please"
date: 2009-02-25
forum: General Help
---

### Post by HIjustme on 2009-02-25
HI all, just registered, thought i'd be needing to post a few questions here in the future as im pretty new to ubuntu/linux.
First of all i'd like to ask how I can start my wireless connection without botting up windows, then restarting and booting ubuntu to get the connection.
Heres some info about my connection if it helps...

Interface : 802.11 WiFi (wlan0)
Driver : rt2400pci
Speed 1mb/s(on windows i always get 11mb/s =[ )

Second question, I would like to install my graphics driver/controller, so I downloaded the folder named dripkg, which has folders inside named agpgart, agpgart-2.0, CVS, drm, gdg, GL, kernel-modules. Then files name Cards, dri.log, dri-I915.spec, install.sh, pkginfo, tmp.log.
After a long time I found out how to run the installer(yes im a newbie).
I did:
sudo -i
[password]
cd /place/where/dripkg/is/
./install.sh

Then I went through the installer,install driver etc etc.
Then I get these errors while it compiles:

Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

Heres the dri.log:
```
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/gareth/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/gareth/dripkg/agpgart-2.0/backend.o
/home/gareth/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:110: error: previous declaration of ‘agp_backend_acquire’ was here
/home/gareth/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:110: error: previous declaration of ‘agp_backend_acquire’ was here
/home/gareth/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:111: error: previous declaration of ‘agp_backend_release’ was here
/home/gareth/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:111: error: previous declaration of ‘agp_backend_release’ was here
/home/gareth/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/gareth/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/gareth/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function ‘inter_module_register’
/home/gareth/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/gareth/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/gareth/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/gareth/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/gareth/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function ‘inter_module_unregister’
make[2]: *** [/home/gareth/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/gareth/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/gareth/dripkg/drm'
make -C /lib/modules/2.6.24-23-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
rm: cannot remove `/home/gareth/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/gareth/dripkg/drm'
make: *** [gdg.ko] Error 2
```

I really hope someone can help me out with these two problems as I really like linux better than XP if only I could do the above things.
Thanks.

---

### Post by HIjustme on 2009-02-25
Anyone please?

---

### Post by abhilashm86 on 2009-02-25
> **HIjustme said:**
> Anyone please?

what is your version of ubuntu, try downloading basic compilers and others in order to execute work easily
i guess ubuntu directly detects wireless during boot up itself(enable wi-fi initially), so ask your question in below wireless and networking,maybe you'll get the answer there,


[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by oldos2er on 2009-02-25
What are the makes/model of your video card and wireless controller?

 For video, assuming you're using Gnome, you would install drivers via the menus System, Administration, Hardware Drivers.

---

### Post by HIjustme on 2009-02-25
> **abhilashm86 said:**
> what is your version of ubuntu
8.04

> For video, assuming you're using Gnome, you would install drivers via the menus System, Administration, Hardware Drivers.
There is nothing there, it says no drivers are in use on this system.

---

### Post by HIjustme on 2009-02-26
Pleeeaase?
:D

---

### Post by mb_webguy on 2009-02-26
Could you open the terminal and run the command "lspci", and then copy and paste the output here?  That way we can see exactly what wireless and video card you're using.

---

### Post by csurlee on 2009-02-26
For the video card if its ati or nvidia you can use ENVYNG

---

### Post by oldos2er on 2009-02-26
> **HIjustme said:**
> Pleeeaase?
:D

 Please post your hardware specs. Until we know, it's difficult to give you useful advice.

---

### Post by HIjustme on 2009-02-26
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:05.0 Network controller: RaLink Wireless PCI Adapter RT2400 / RT2460
01:07.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
01:0d.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by oldos2er on 2009-02-27
Try installing the package xserver-xorg-video-intel .

---

### Post by HIjustme on 2009-02-27
Didn't work. :(

---

### Post by Yellow Pasque on 2009-02-27
Why were you trying to compile video drivers? The video driver should be installed and working "out of the box".

Please post the output of this command, in a [ CODE ][ /CODE ] block.
```
cat /etc/X11/xorg.conf
```

---

### Post by HIjustme on 2009-02-27
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by HIjustme on 2009-02-27
> **Temüjin said:**
> Why were you trying to compile video drivers?
Because I play ET, on xp I had like 40 fps average, and I heard Linux gives better fps, so reason is beause I dont think the driver is installed because i get 30 fps sometimes 40.

---

### Post by Yellow Pasque on 2009-02-27
Can you post the output of:
```
LIBGL_DEBUG=verbose glxinfo
```
I don't think there's any issue with your driver setup, other than the version of intel driver included in Ubuntu 8.x doesn't perform as well as the Windows driver. Look for this to change in Ubuntu 9.04 & 9.10

---

### Post by HIjustme on 2009-02-27
```
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 1.9.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
libGL error: 
Can't open configuration file /etc/drirc: No such file or directory.
libGL error: 
Can't open configuration file /home/gareth/.drirc: No such file or directory.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by Yellow Pasque on 2009-02-27
Your glxinfo looks fine. You can try tweaking DRI settings with the driconf package, but IMHO, you don't really have an issue here.

---

### Post by HIjustme on 2009-02-27
Oh.. but what about where it says at the eng of the bottom lines: slow, none.
Does it mean its on slow settings so if i change it to fast or something wont i get better fps?
Thanks for your help mate.

---

### Post by Yellow Pasque on 2009-02-27
No, glxinfo is just reporting all of the glx modes your driver supports. It doesn't mean your driver is using the modes marked as 'slow'.

---

### Post by HIjustme on 2009-02-27
Ok, how can I tweak DRI settings? Where can I find the driconf?
Thanks mate.

---

### Post by Yellow Pasque on 2009-02-27
You can install driconf through Synaptic or in terminal:
```
sudo apt-get install driconf
```
You can then launch it under System -> Preferences -> 3D Acceleration

I don't know if you'll find any settings to increase your FPS, but it's worth a try. Another way to increase your video performance could be allocating more RAM to the video card in the BIOS (if such an option exists).

As for your wireless problem, can you post output of:
```
sudo lshw -C network
```

---

### Post by HIjustme on 2009-02-27
```
  *-network:0             
       description: Wireless interface
       product: Wireless PCI Adapter RT2400 / RT2460
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wmaster0
       version: 00
       serial: 00:11:09:08:18:f6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2400pci ip=192.168.1.64 latency=32 module=rt2400pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 01
       serial: 00:11:09:fc:a2:5f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
```

What settings do I need to set in 3D Acceleration to get best performance? I don't understand what all the options mean :(

Thanks.

---

### Post by HIjustme on 2009-03-01
> As for your wireless problem, can you post output of:

```
sudo lshw -C network
```
Here:
```
*-network:0             
       description: Wireless interface
       product: Wireless PCI Adapter RT2400 / RT2460
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wmaster0
       version: 00
       serial: 00:11:09:08:18:f6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2400pci ip=192.168.1.64 latency=32 module=rt2400pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 01
       serial: 00:11:09:fc:a2:5f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
```

---

### Post by HIjustme on 2009-03-04
Lil bump

---

### Post by HIjustme on 2009-03-04
Got another question to ask, not sure whether its in the correct section, but i'd like to know how can i get my mic to work on Ventrilo?(through wine ofc).

---

### Post by Yellow Pasque on 2009-03-05
If the native linux wireless driver doesn't work for you, you can try using a windows driver and ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

