---
title: "Z-buffer problem on a SiS630S-based laptop."
date: 2005-06-13
forum: Desktop Environments
---

### Post by Tomasz on 2005-06-13
This is a SiS630S-based laptop, SiS6326 graphics core (with a tvout suprisingly working in ubuntu).  I've followed the guide at winishhofer.at and I have to most recent drivers installed, glxinfo showing OpenGL operational (or not? I'm confused now):

```
root@ubuntu:/home/dom # glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIS_multisample,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Eric Anholt
OpenGL renderer string: Mesa DRI SiS 20040925 AGP 1x x86/MMX/SSE
OpenGL version string: 1.2 Mesa 6.2.1
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, GL_MESA_window_pos,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

However, running an OpenGL-base screensaver gives me a blank screen, and a simple benchmark glxgears returns an error:

```
root@ubuntu:/home/dom # glxgears
[sis_alloc.c:154]: Failure to allocate Z buffer.
```

There's not much information on the Internet about this problem, can you help me out? Years ago on Win98 I could run every game I wanted using OpenGL or DX. Three simple cogwheels can't show up in Linux?  I hope this is a user error... Though there was not much to configure, sisctrl is a good tool for tweaking brightness, tv modes, etc, but no OpenGL settings there.
 
Laptop configuration:
Uniwill N340S8
SiS630S Rev49 chipset (SiS6326 graphics, SiS7018 sound, SiS900 NIC)
384MB RAM (-32MB given to graphics makes about 352MB)
Ubuntu 5.04

---

### Post by Swoop on 2005-06-15
Well i can say i have the exact same problem... dont know a darn thing about it exept that i suspect that the sis drivers arent good enough (not complaining about the bloke doing them for free) .. stupid company not supporting linux :( 

Anyways please do let me know if you find out something about it.. as will i if i ever get it working :(

---

### Post by mpa on 2005-06-15
Check the FAQ ([http://www.winischhofer.at/linuxsispart3.shtml#faq](http://www.winischhofer.at/linuxsispart3.shtml#faq))


4. Hardware accelerated 3D (DRI/OpenGL)
Q: Tuxracer is terribly slow on my SiS315/550/650/651/M650/330/661/741/760
A: DRI and hardware accelerated OpenGL/3D is not supported on these chipsets. I don't know how many times I must say this. And besides, I don't do any DRI related development. Complaints should be sent to the DRI project's mailing lists (dri.sf.net)
 
Q: I installed XFree 4.3 and I don't have 3D support anymore on my 300 series chipset. What's wrong?
A: Due to the inclusion of Mesa version 4 in XFree 4.3, the SiS DRI driver was disabled because nobody converted it to Mesa 4. You can still use Mesa version 3 which came with XFree 4.2. Debian users may just install the xlibmesa3 packages from 4.2 (which are available in the download section on this page.) Users of other distributions should backup all existing libGL.so*, libGLU.so* files as well as all files in /usr/X11R6/lib/modules/dri/ before installing XFree 4.3. After that simply copy them back to their old locations. But beware: The DRI driver files *must* have been compiled with the same version of gcc as the X server. Update: An updated DRI driver is in XFree86 4.3.99.14, meaning that there is no such workaround required if you are using this version or later.
 
Q: I have problems with DRI.
A: Please stop asking me questions about DRI. All information I have is available at my DRI page. And no, I do not develope anything DRI related. Please contact the DRI project for problems with DRI/OpenGL/hardware accelerated 3D. I have a sis DRI driver in my download section which has been reported to work fine. Try that if you like. Otherwise I can't help you.

---

### Post by Swoop on 2005-06-15
Already read that.. and i still dont see my own problem.

My gfx card however (didnt notice the difference) is 630 (300 series) which IS supported, and thus i dont understand why it doesnt work at all :(

Standard install ubuntu doesnt use the xfree does it .. anyways im using xorg 6.80.2 i believe and thus again it should be working according to that site. Btw im using his sis drivers (and same problem before instlaling them) ..

So im still basically at a loss for what to do :(

---

### Post by Enkurs on 2005-06-20
I have a laptop with SiS M650 chipset, and everywhere on the Internet i find information, that the chipset doesn't support hardware acceleration.

But then, how come under Windows many Direct3D / OpenGL games are working pretty snappy.. (or at least a quite faster than tuxracer on Linux) Somehow it doesn't seem it's done all just by the CPU.

Is there a chance that someday SiS will release the chipset documentation and we'll be able to see some hardware acceleration under Linux also?

Anyway, Linux is not for games, so i didn't open a new thread for this. :)

---

### Post by sercz on 2005-06-30
[QUOTE=Swoop]
My gfx card however (didnt notice the difference) is 630 (300 series) which IS supported, and thus i dont understand why it doesnt work at all :(

Standard install ubuntu doesnt use the xfree does it .. anyways im using xorg 6.80.2 i believe and thus again it should be working according to that site. Btw im using his sis drivers (and same problem before instlaling them) ..
[/QUOTE]

I also have a sis730 notebook and exactly your problem.

Of course you are using Winschhofers drivers, because (from his site): "Installing any driver from this website does not mean installing some sort of "third party" software. I am, in fact, the author and maintainer of both the official X.org and XFree86 SiS driver as well as the Linux kernel's SiS framebuffer driver."

By the way: I had glxgears successfully working with hardware acceleration using  gentoo on my notebook, but I had a lot to do by hand...

Two things I found out till now:
I used to use the kernel module "sisfb" with gentoo; Winischhofer says, this is a requirement for dri. But when I modprobe it here, "dmesg" tells me:
```

sisfb: Video ROM found and mapped to 0xc00c0000
sisfb: Fatal error: Unable to reserve frame buffer memory
sisfb: Is there another framebuffer driver active?

```

I found in /var/log/Xorg.0.log:
```

(==) SIS(0): DRI enabled
(...)
(II) SIS(0): [dri] DRI video RAM memory heap: 0x0 to 0x0 (0KB)
(...)

```

I will keep an eye on this thread and post if I figure out more...

greets

---

### Post by Tomasz on 2005-08-23
Problem solved, just get new a new driver from Winishhofer.net :)

```
dom@ubuntu:~$ glxgears
754 frames in 5.0 seconds = 150.800 FPS
1023 frames in 5.0 seconds = 204.600 FPS
1023 frames in 5.0 seconds = 204.600 FPS
942 frames in 5.0 seconds = 188.400 FPS
```

Not exactly a performance beast, that SiS630. ;)

---

