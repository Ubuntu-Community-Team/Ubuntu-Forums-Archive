---
title: "How do i run urban terror!?"
date: 2008-11-29
forum: Gaming &amp; Leisure
---

### Post by Zaerdna on 2008-11-29
Ok so ive downloaded urban terror the linux/mac zip and ive extracted everything and i cant run it! if i try to open any of the .exe's it never start even if i change so i can run and write and open with program starter or whats its called. I just cant run it do i have to type something in the terminal? please help me!

also: do i need to install any 3D thing like directX for windows pc's cos i dont't know that either :(


PLEASE, PLEASE HELP ME!:confused:

---

### Post by Perfect Storm on 2008-11-29
64-bit guide; [http://gaming.gwos.org/doku.php/guides:64bit:urban_terror](http://gaming.gwos.org/doku.php/guides:64bit:urban_terror)

If you're running 32-bit you need to adjust the guide thereafter.

---

### Post by Azure.Rise on 2008-11-29
The executable file is oUrbanTerror.i386 have you tried running that? And no you shouldn't have to install anything extra. Try running that file, if it doesn't open run it in the terminal to see if it gives you any errors.

---

### Post by wowgoods on 2008-11-29
[buy wow gold](http://www.vcsale.com/)
[cheap wow gold](http://www.vcsale.com/)
[wow gold](http://www.vcsale.com/)
[cheapest wow gold](http://www.vcsale.com/)
[warhammer gold](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)
[warhammer powerleveling](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)
[war gold](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)
[war powerleveling](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)
[war power leveling](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)
[buy wow gold](http://www.vcsale.com/)
[cheap wow gold](http://www.vcsale.com/)
[wow gold](http://www.vcsale.com/)
[cheapest wow gold](http://www.vcsale.com/)
[warhammer gold](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)
[warhammer powerleveling](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)
[war gold](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)
[war powerleveling](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)
[war power leveling](http://www.vcsale.com/service.Warhammer_Online_US.31.aspx)

---

### Post by Zaerdna on 2008-11-30
> **Azure.Rise said:**
> The executable file is oUrbanTerror.i386 have you tried running that? And no you shouldn't have to install anything extra. Try running that file, if it doesn't open run it in the terminal to see if it gives you any errors.

Yeah i tried that and its just loading and after like 6 seconds it closes down! but im new to ubuntu/linux so what do i type in terminal?:confused:

---

### Post by eragon100 on 2008-11-30
> **Zaerdna said:**
> Yeah i tried that and its just loading and after like 6 seconds it closes down! but im new to ubuntu/linux so what do i type in terminal?:confused:

./ioUrbanTerror.i386

---

### Post by Azure.Rise on 2008-12-03
Have you tried turning Compiz-Fusion off? That caused some problems for me with Urban Terror.

---

### Post by bibleman on 2008-12-03
First of all do you even have Direct Rendering working on your machine? As far as I know you need that to play Urban Terror. You can check that by typing *glxinfo* into the terminal. Somewhere in there it says Direct Rendering and it should say yes by it. If it doesn't then you need to install drivers for your graphics card.

What was the error in the terminal?

I will also ditto the Compiz problems. I have intermittent problems though, but the program still works. If that is the problem you will need to switch to a different window manager like Metacity.

---

### Post by Zaerdna on 2008-12-03
> **bibleman said:**
> First of all do you even have Direct Rendering working on your machine? As far as I know you need that to play Urban Terror. You can check that by typing *glxinfo* into the terminal. Somewhere in there it says Direct Rendering and it should say yes by it. If it doesn't then you need to install drivers for your graphics card.

What was the error in the terminal?

I will also ditto the Compiz problems. I have intermittent problems though, but the program still works. If that is the problem you will need to switch to a different window manager like Metacity.

when  typed glxinfo this came up

display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061102 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_point_sprite, GL_NV_texture_rectangle, GL_NV_texgen_reflection, 
    GL_NV_vertex_program, GL_NV_vertex_program1_1, GL_OES_read_format, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x56 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x57  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x58  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x59  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5a  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5b  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x5c  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x5d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x5e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x61  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x62  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x63  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x64  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x66  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x67  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x69  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6a  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6b  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6c  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6e  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6f  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x70  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x71  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x72  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x73  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x74  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x75  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x76  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x77  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x78  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x79  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow


and i have a laptop and im not sre it has a graphic card :S

---

### Post by bibleman on 2008-12-03
I am not sure that the integrated graphics will cut the mustard for Urban Terror. Try typing this into a terminal
```
lspci
```
Somewhere in there you should see entry like
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000]
```
That is the card on my laptop by the way. Once you figure out what graphics card it has then you can install the drivers for it. If it doesn't have a graphics card then you might not be able to play Urban Terror.

---

### Post by Zaerdna on 2008-12-04
> **bibleman said:**
> I am not sure that the integrated graphics will cut the mustard for Urban Terror. Try typing this into a terminal
```
lspci
```
Somewhere in there you should see entry like
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000]
```
That is the card on my laptop by the way. Once you figure out what graphics card it has then you can install the drivers for it. If it doesn't have a graphics card then you might not be able to play Urban Terror.

when i typed this came up

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 
943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition

and some other things but the rest was nothing about graphic

---

### Post by maddog46113 on 2008-12-04
> **Zaerdna said:**
> Yeah i tried that and its just loading and after like 6 seconds it closes down! but im new to ubuntu/linux so what do i type in terminal?:confused:

to launch it in terminal you can do two things, type out the directory to wherever you have it like:
"/home/user/urbanterror/ioUrbanTerror.i386 "

OR you can open terminal and click the file itself and simply drag it into the terminal then hit enter then it should tell you something or another when it crashes. Copy and paste the error it gives you.

---

### Post by Zaerdna on 2008-12-04
> **maddog46113 said:**
> to launch it in terminal you can do two things, type out the directory to wherever you have it like:
"/home/user/urbanterror/ioUrbanTerror.i386 "

OR you can open terminal and click the file itself and simply drag it into the terminal then hit enter then it should tell you something or another when it crashes. Copy and paste the error it gives you.


when i change the permission to "enable to execute file as a program" this comes up:

andreas@andreas-laptop:~$ '/home/andreas/Dokument/UrbanTerror/ioUrTded.i386' 
ioq3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Current search path:
/home/andreas/.q3a/q3ut4
/home/andreas/Dokument/UrbanTerror/q3ut4/zpak000_assets.pk3 (7933 files)
/home/andreas/Dokument/UrbanTerror/q3ut4/zpak000.pk3 (99 files)
/home/andreas/Dokument/UrbanTerror/q3ut4

----------------------
8032 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: andreas-laptop
IP: 127.0.1.1


if i dont change the permission it says permission denined

---

### Post by Bananaloaves on 2008-12-04
I dual boot Mac OSX and Ubuntu. I currently downloaded the mac version of urban terror. I'm wondering what are the differences, if any, of running it in mac or ubuntu? Also, I have open arena and i added a bunch or character models. Does urban terror allow me to add character models?

---

### Post by bibleman on 2008-12-04
According to what you posted you only have Intel Integrated Graphics. As far as I know you cannot run Urban Terror without an Nvidia or ATI card with at least 128MB of RAM.

---

### Post by Bananaloaves on 2008-12-04
> **bibleman said:**
> According to what you posted you only have Intel Integrated Graphics. As far as I know you cannot run Urban Terror without an Nvidia or ATI card with at least 128MB of RAM.


I can run urban terror with an intel card. I have a GMA 950, and it works fine.

---

### Post by eragon100 on 2008-12-04
> **bibleman said:**
> According to what you posted you only have Intel Integrated Graphics. As far as I know you cannot run Urban Terror without an Nvidia or ATI card with at least 128MB of RAM.

It's based on the quake 3 engine and is known for low system requirements.

Tremulous, which runs on the same engine and is also an FPS, gets an average of 32 frames per second at 1280x960 res on that card. Urban terror will run fine on it :wink:

---

### Post by bibleman on 2008-12-04
Thanks for the clarification but I was just saying from everything I have found on the internet and my own personal experience.

"fine" is a very vague word btw. Will it run? maybe but don't count on it running very well. I wouldn't count 32 fps fine...

---

### Post by juanoleso on 2008-12-04
I think that you are trying to run the wrong file.

Open home folder (places -> Home Folder)
double click Dokument
double click UrbanTerror
right click ioUrbanTerror.i386
click permissions tab
make sure Execute: is checked
hit close
double click ioUrbanTeror.i386

or in terminal:
```
cd /home/andreas/Dokument/UrbanTerror/
chmod a+x ./ioUrbanTerror.i386
./ioUrbanTerror.i386
```

I don't know for sure because I haven't tried it, but I believe that ioUrTded.i386 is to start a dedicated none graphic server...

---

### Post by Azure.Rise on 2008-12-04
After you type that in the terminal do you get any errors?

---

### Post by Zaerdna on 2008-12-05
> **juanoleso said:**
> I think that you are trying to run the wrong file.

Open home folder (places -> Home Folder)
double click Dokument
double click UrbanTerror
right click ioUrbanTerror.i386
click permissions tab
make sure Execute: is checked
hit close
double click ioUrbanTeror.i386

or in terminal:
```
cd /home/andreas/Dokument/UrbanTerror/
chmod a+x ./ioUrbanTerror.i386
./ioUrbanTerror.i386
```

I don't know for sure because I haven't tried it, but I believe that ioUrTded.i386 is to start a dedicated none graphic server...

if i type that it actually runs! it works! only problem is..whenever i open a quake 3 based game after some seconds in the menu it gets all black and the cursor change to a red square and i cant see "start game" or "new server" things :( maybe i have to change resoluton settings
??

---

### Post by maddog46113 on 2008-12-05
Do you have Compiz running, if so try turning it off?

---

### Post by maddog46113 on 2008-12-05
I found this 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/120834](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/120834)

a little ways down the page someone confirms the same problem with your card.
he said it drastically decrease performance so its your call.
if you want to try it you need to:

first be sure you back this file before you change it!!

open terminal
```

sudo gedit /etc/X11/xorg.conf

```

add this under the Section "Device"
```

Option "DRI" "false"

```

save and exit the editor

press ctrl + backspace (make sure you dont have anything unsaved going

then log back in and try to run your game. Let me know if it worked! Good Luck!
PS: If you dont like what it does then simply follow the directions again and remove the line.

---

### Post by Zaerdna on 2008-12-05
> **maddog46113 said:**
> Do you have Compiz running, if so try turning it off?

nope

---

### Post by Zaerdna on 2008-12-05
> **maddog46113 said:**
> I found this 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/120834](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/120834)

a little ways down the page someone confirms the same problem with your card.
he said it drastically decrease performance so its your call.
if you want to try it you need to:

first be sure you back this file before you change it!!

open terminal
```

sudo gedit /etc/X11/xorg.conf

```

add this under the Section "Device"
```

Option "DRI" "false"

```

save and exit the editor

press ctrl + backspace (make sure you dont have anything unsaved going

then log back in and try to run your game. Let me know if it worked! Good Luck!
PS: If you dont like what it does then simply follow the directions again and remove the line.

do you mean it should look like this?

Section "Device"
	Option "DRI" "false"	"Configured Video Device"

---

### Post by maddog46113 on 2008-12-05
no like this 

Section "Device"
	Identifier	"Configured Video Device"
        Option "DRI" "false"

---

### Post by bibleman on 2008-12-06
Just in case anyone was wondering the ioUrTded executable will start a dedicated server. That's why it seemed as though nothing had happened when he started it. All that happened is he started up a local server that others on his local network could connect to.

---

### Post by stinger30au on 2008-12-06
[this tutorial by a french ubuntu team may help you out]("http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/urban_terror&sa=X&oi=translate&resnum=6&ct=result&prev=/search%3Fq%3Dubuntu%2Burban%2Bterror%26hl%3Den%26client%3Dopera%26rls%3Den%26hs%3DKat")

---

### Post by Zaerdna on 2008-12-06
> **maddog46113 said:**
> no like this 

Section "Device"
	Identifier	"Configured Video Device"
        Option "DRI" "false"

that only made ever game unplayable it laggs so much

---

### Post by maddog46113 on 2008-12-06
:(

---

### Post by Sea_of_fear on 2009-01-03
I just run the ioUrbanTerror.exe file with wine. It works very well.

Wine is a program with which you can run some windows programs, games, so on. 

You should have Wine installed already with Ubuntu. Actually it should open it automatically. Mine did altho mine isn't Ubuntu 100% altho it was build on it. I use PC/OS 2009. The funny thing is I can't figure out how to run the .i386 version of it lol

Ok I would try to right click the ioUrbanTerror.exe file and choose open with.. then find Wine. 

Might also work just to open terminal in folder and type: wine ioUrbanTerror.exe. But I haven't tried that because I don't have to. lol

Good luck.

---

### Post by Rafdog on 2009-01-03
I don't think he should start messing with WINE if urban Terror runs natively on Linux via the proper file.  He can run the game but the screen starts to get all jumbled and you cannot read any of the menu's.  Even with all graphics settings set to minimum he will have some issues.  I had the same problem when I got into Urban Terror.  Luckily I had a mobo with an PCIE slot, so I went and bought a ATI graphics card, installed the proper xserver, reconfigured and viola!

He might have to mess with the configuration files in the Urban Terror folder to get the settings down to  minimum and work up from their.

---

### Post by StarryTripper on 2009-01-18
I installed Urban Terror with "sudo aptitude install urbanterror" after adding the getdeb repository.

deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/

I'm running with a GeForce 4 64MB and it runs fine.

I had to turn off Visual Effects in System>Preferences>Appearance or most of the time (but not all, which was weird) after starting in Fullscreen it would drop to windowed and my cursor would be all screwed up.

I'd have to move to another console and kill it. Sometime I couldn't get cursor back without restarting X.

After setting Visual Effects to None though, no problems.

---

### Post by gjoellee on 2009-01-18
Follow this easy tutorial: [http://www.kshoster.net/content/howto-install-urban-terror-linux](http://www.kshoster.net/content/howto-install-urban-terror-linux)

or download the DEB file from [www.GetDeb.net](www.GetDeb.net) (found in the Games section for Ubuntu Hardy Heron, it works on all Ubuntu versions though).

---

