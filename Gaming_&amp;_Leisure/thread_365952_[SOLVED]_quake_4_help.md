---
title: "[SOLVED] quake 4 help"
date: 2007-02-20
forum: Gaming &amp; Leisure
---

### Post by Homunculi on 2007-02-20
i just need a little help with the quake 4 engine ](*,) 
booting back and forth looking at the start up of windows xp  and linux quake4 init 
i notice this in the linux start of quake 4:
------ Common Initialization Complete -------
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 7103
detecting video ram ( set sys_videoRam to force ) ..
**guess failed, return default low-end VRAM setting ( 64MB VRAM )**
2793 MHz CPU
1008 MB System Memory
64 MB Video Memory
Async thread started
guid set to otdz5I0JcK0

in the terminal init i get this video ram setting and i have tried xfce and kde
same results
in windows it is set to 256mb of memory that the card has onboard 
my system is as follows:
intel p4 2.8ghz
1gb ram 
2 250gb 16mb cache seagate drives
sound blaster audigy
ati X1300 agp 256mb
2 plextor dvd drives 
3com 10/100 nic
usb kb and mouse 

i know my system is a little antiquated but i look at the requirements for quake 4 and i exceed them in cpu memory and video ... 
and help would be very welcome 

i have plans on a upgrade to nvidia and a amd cpu .. but i would like to get inti the game till then :)  
thank you

---

### Post by Homunculi on 2007-02-20
sorry .. forgot this info 
fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

glxinfo:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

---

### Post by temba on 2007-02-20
Hi there,

in your post it says :detecting video ram ( set sys_videoRam to force ) ..

When loading quake (in a terminal) try "quake4 set sys_videoRam 256" - or maybe even 128 to start with

Also check this site for a good guide to different options to run at startup - [www.tweakguides.com](www.tweakguides.com) - it did wonders for me!

happy quaking and let us know how you got it to work for you.

cheers

---

### Post by Homunculi on 2007-02-20
thank you 
help out alot ... at least playable with the vm setting .
will check out the tweak guides ... 

thanks again  


terminal support enabled ( use +set in_tty 0 to disabled )
pid: 4783
sys_videoRam: 256
2792 MHz CPU
1008 MB System Memory
256 MB Video Memory
Async thread started
guid set to otdz5I0JcK0
------------ Game Map Shutdown --------------

---

