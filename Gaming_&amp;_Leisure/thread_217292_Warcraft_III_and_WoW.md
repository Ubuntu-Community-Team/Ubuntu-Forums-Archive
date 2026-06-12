---
title: "Warcraft III and WoW"
date: 2006-07-16
forum: Gaming &amp; Leisure
---

### Post by Sp00ne on 2006-07-16
Ive got wine working pretty well, but when it comes to Warcraft III and WoW, it just wont work.

I put in this command to get WoW up and running ```
wine "/home/ben/.wine/c/Program Files/World of Warcraft/WoW.exe"
``` And press enter then this comes up: 

[[IMG]http://img132.imageshack.us/img132/5586/screenshotsi3.th.png[/IMG]](http://img132.imageshack.us/my.php?image=screenshotsi3.png)

Do i just update my drivers? Any good help would be appriciated.

And as for Warcraft, i put in ```
wine "/home/ben/.wine/c/Warcraft III/war3.exe
```

It loads, then just freezes and i have to restart my laptop.

---

### Post by eqisow on 2006-07-16
In regards to WoW, are you running the version of Wine patched for WoW? If not, check [here]("https://help.ubuntu.com/community/Wine") and follow the instructions under "Latest Wine with WoW Patch".

Even if you're not, that's a very odd error. I've never seen it before. Try running the following command to be sure 3D acceleration is working:
```
glxinfo | grep direct
```
You should see "direct rendering: Yes" as output. If you don't then we'll need to work on getting your 3D set up. If you do, then I'm not completely sure how to proceed.

As for WCIII, try setting Wine to run programs inside a virtual desktop. It will be under graphics in winecfg. This way you should be able to see the console output when you try to run it, and also be able to kill it without restarting X. Paste the terminal output here.

You could also check Wine's [application database]("http://appdb.winehq.org") for tips.

---

### Post by Sp00ne on 2006-07-16
Ok, "direct rendering :Yes" came up, and ill try running WCIII in a virtual desktop in a second.

Update: I ran WCIII in the virtual desktop, all that happened was it showed a small part of the start up movie, then exited.

---

### Post by Cure777 on 2006-07-16
Virtual desktop? I'll have to try that with Wine. I'm sick of having to restart Ubuntu just cuz something crashed or messed up the resolution](*,)

---

### Post by eqisow on 2006-07-16
Sp00ne, maybe Wine doesn't have the proper codec for viewing the video, and thus crashes? Try mulling about your WCIII configs and see if you can turn the video off somehow.

Also, what video card are you using?

---

### Post by Sp00ne on 2006-07-17
I dont know what video card i have, it just have the default card that came in/with the laptop.

---

### Post by vem0m on 2006-07-17
i would make sure ur drivers are installed right goto terminal and type "glxinfo" and post here what it says

---

### Post by Sp00ne on 2006-07-17
i typed in "glxinfo" and this came up:
> name of display: :0.0
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
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
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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


---

### Post by vem0m on 2006-07-17
yea u are not running with 3d accelleration u are using MESA crap try to find out what is ur GFX chips' vendor then get the proper drivers from them

---

### Post by Sp00ne on 2006-07-17
How do i do that?

---

### Post by eqisow on 2006-07-17
Post the output of lspci and we should be able to tell you. :)

---

### Post by Sp00ne on 2006-07-17
I typed in "lspci" and it came up with
> 0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express P
rocessor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GM
L Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Expre
ss Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FR                   W (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97                    Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge                    (rev 04)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (                   rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus                    Controller (rev 04)
0000:01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C                   ontroller (PHY/Link)
0000:01:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re                   v 02)
0000:01:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:01:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev                    10)
0000:01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader C                   ontroller (rev 01)
0000:01:04.2 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Control                   ler (rev 01)
0000:01:04.3 FLASH memory: ENE Technology Inc: Unknown device 0520 (rev 01)
0000:01:04.4 FLASH memory: ENE Technology Inc: Unknown device 0551 (rev 01)


---

### Post by Cure777 on 2006-07-17
> george@george-desktop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub  Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (re v 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI  Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface  Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Contro ller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (re v 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller ( rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH 5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Fir eGL 9000] (rev 02)
0000:02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
0000:02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Cont roller (rev 02)
george@george-desktop:~$

That's what it tells me. I know I have an ATI Radeon Mobility All-In-Wonder 9000 Pro, but I have no idea where or what drivers to get:confused:

---

### Post by vem0m on 2006-07-17
Simple Cure777 use [THIS GUIDE]("http://ubuntuforums.org/showthread.php?t=204910")

sp00ne i dunno bout urs as u have a Intel chip not a nvidia nor a ATi so urs is trickier maybe someone else will be able to help

---

### Post by Sp00ne on 2006-07-17
Thanks for your help so far.

But im just annoyed that this 3d acceleration thing has come up, but it(WoW) worked fine with windows.

---

### Post by vem0m on 2006-07-17
yes as windows automatically(well alot of the time with a GFX chip such as urs) sets it up for you here u gotta get the proper drivers if any and pray to god that it works

---

### Post by Sp00ne on 2006-07-17
By drivers do you mean cards, or downloadbale ones?

---

### Post by vem0m on 2006-07-17
drivers are software to make ur hardware work so i mean the only one there is which is download

---

### Post by Sp00ne on 2006-07-17
Which drivers do i need? (im a bit of a newb to linux)

---

### Post by vem0m on 2006-07-17
like i said before i just know ur chipset seems to be Intel and i have no clue on those generic things i would suggest u figure out which card u have of intel, goto thier site and check for linux drivers for it. Other then that my recommendation if do-able is to get a new GFX Card i would suggest ATi :)

---

### Post by tuxcantfly on 2006-07-18
cat /etc/X11/xorg.conf

check the driver section, it should say something like

nv
nvidia
ati
radeon

---

### Post by Sp00ne on 2006-07-18
I searched through, none of those were mentioned, the closest for "ati" was in the words "configuration" and "automatically".

---

### Post by vem0m on 2006-07-18
it won't say ati nv nvidia or any of that he has a Intel chip LMAO

---

### Post by tuxcantfly on 2006-07-18
what does it say under the driver section, then? i810 or something?

---

### Post by Sp00ne on 2006-07-18
Yeah, it says that.

---

### Post by vem0m on 2006-07-18
so if it says i810 goto intels website and find a linux drivers for that chip i dunno the exact install precedures but shouldn't be hard to get it then u should have it working

---

### Post by tuxcantfly on 2006-07-18
maybe fetch a newer driver from here:

[http://www.beerorkid.com/compiz/pool/aiglx/x/xserver-xorg-driver-i810/](http://www.beerorkid.com/compiz/pool/aiglx/x/xserver-xorg-driver-i810/)

also, do you have dri and glx enabled?

---

### Post by tuxcantfly on 2006-07-18
by the way, do NOT get drivers from intel; they're designed for older xserver versions (xfree86 3.x and xorg 6.x) while ubuntu uses xorg 7.x; installing drivers from intel will probably break your system

---

### Post by vem0m on 2006-07-18
most drivers are for 6.x as 7.0 is really new

---

### Post by Sp00ne on 2006-07-18
Ok, i got the driver, how do i install it/them? (sorry, but im a real newb to this).

---

### Post by tuxcantfly on 2006-07-19
get the one that ends in .deb

then, just do

sudo dpkg -i /path/to/your/downloaded/package.deb

---

### Post by tuxcantfly on 2006-07-19
it might not even be an issue with the drivers, though. check to see if you have libgl1-mesa and libgl1-mesa-dri installed and that under the modules section in /etc/X11/xorg.conf, you have glx and dri, and that glcore is disabled (commented out or not there at all)

---

