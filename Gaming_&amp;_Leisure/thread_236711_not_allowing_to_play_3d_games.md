---
title: "not allowing to play 3d games?"
date: 2006-08-15
forum: Gaming &amp; Leisure
---

### Post by fblade1987 on 2006-08-15
hey guys i have recently tried to install bzflag on ubuntu and it dosent work you click to run and a winodow pops up for a fraction of a seccond then closes, so i just thought it was a currpted copy, so then i tried running the linux version of savage, that did the same. 

so at this point i decieded to run the games through the console but because im still a linux n00b i tried typing them two diffrent ways but still both gave me a error but they where diffrent.

1.when i typed ./bzflag or ./savage i got this error.
> /home/matt/game/bin/./../lib/OBLISK/bzflag-2.0.8/bin/bzflag: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory


2. when i typed just bzflag or just savage i got this one.
> X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3e
  Serial number of failed request:  122
  Current serial number in output stream:  124



can any1 help me figure this out please
thanks fblade

---

### Post by geokok1981 on 2006-08-15
Not sure at all about this but here goes nothing...
Do you have 3D acceleration activated?What vga u have and have u 
installed the drivers?
Do u get slow 3d screensavers as well (ie try the 3d ants to see)

---

### Post by fblade1987 on 2006-08-15
well i did istall the ati driver off the sti site for radeon x700 and the 3d ants screensaver works pritty well how can i see if 3d aceleration is activated?

edit~ dunno if this will be any help aswell just tried useing 3d desktop and i got this error
> 3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.


edit 2 ~ i just had the screen saver work full screen and it is slightly sluggish

---

### Post by lupine_nickt on 2006-08-15
When you get something like:-

> 
/home/matt/game/bin/./../lib/OBLISK/bzflag-2.0.8/bin/bzflag: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory


It means that you need to install the library that's missing - in this case, that's libSDL_image (version is 1.2)

So, 'sudo apt-get install libsdl_image' should work.

If that's not the right package, 'apt-cache search libsdl' will give you a list of packages to browse through, until you find the right one.

There's probably other libraries missing as well -- so wash, rinse, repeat until you've got them all installed.

xF,

...Nick

---

### Post by geokok1981 on 2006-08-15
Sorry my mistake. To see if the vga is properly found, type these
in a terminal:
fglrxinfo
glxinfo

---

### Post by fblade1987 on 2006-08-15
doing glxinfo i get this
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None

```

with doing fglxinfo i get this ```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

and nick i tried doing as you said i can install libsdl1.2-image but dosnt allow me to run libsdl1.2-image_dev  saying some of the dependancies are unresolveable

i also tried running bzflag again in terminal and i just get this no matter which way i type bzflag or ./bzflag

> X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3e
  Serial number of failed request:  122
  Current serial number in output stream:  124


---

### Post by lupine_nickt on 2006-08-15
Well, you're running the Mesa OpenGL implementation, which is wrong - but I've got an nVidia card, so I've no idea how you'd fix it on ATi. 

Regarding libSDL_image, make sure that you've got main, restricted, universe and multiverse repositories enabled. Run apt-get update, and apt-get upgrade. Try "apt-get -f install". If none of that works, try to install each dependancy individually - they are:-

libc (you'll have this in already!)
libjpeg62
libpng12-0
libsdl1.2debian 
libtiff4
zlib1g

xF,

...Nick

---

### Post by lupine_nickt on 2006-08-15
Oh, and just so you know - the Savage Linux client is a PITA to get working. It's got unresolved dependencies galore, and uses out-of-date libraries (well, they're out of date *now*...)

Last time I tried it, I managed to get the game to load up but the floor was missing... very off-putting!

xF,

...Nick

---

### Post by fblade1987 on 2006-08-15
well i have all those installed so im lost yet again :neutral: 

and can any1 help me with the Mesa OpenGL problem thanks

---

### Post by geokok1981 on 2006-08-15
How did you install your drivers (if at all)?
Check out the guide here if u like (I recommend method 1)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

---

### Post by fblade1987 on 2006-08-15
That how i installed the drivers, using method 1 i had no errors appear at all installing them so i dont think its the drivers

---

### Post by geokok1981 on 2006-08-15
Ok....my knowledge can only take u that far then. You ll need someone more experienced for help.
But I can tell you the following:
Search the forum. I am pretty sure some other people had similar problem.
If you dont find anything on the forum (unlikely not to, but do go beyond the first 2-3 result pages) connect to the irc channel #ubuntu and tell your problem there.
good luck mate....and next time buy nvidia (or intel if you dont care for games)...it really saves a lot of trouble (ati user here).

---

### Post by fblade1987 on 2006-08-15
> **lupine_nickt said:**
> Well, you're running the Mesa OpenGL implementation, which is wrong - but I've got an nVidia card, so I've no idea how you'd fix it on ATi......


just a note i have manage to now get it to of mesa opengl and onto ati now 
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 Generic
OpenGL version string: 2.0.5946 (8.27.10)


but still the same problem

---

### Post by geokok1981 on 2006-08-15
Would you care to share how you did it for others to read if needed?
If you type glxinfo and you see "3d render : yes" on the first lines everything should work......as I said though u 'll have to hope that someone more experienced sees your problem.

By the way u seem to have the latest drivers. I am running the previous version on a "mobility x700" that I installed using method 1 from the link I gave u and it works perfectly so far (games dont fly cause ati sucks but that 's another story).

---

### Post by fblade1987 on 2006-08-16
i Just reinstalled the drivers using method 2 on the site you pre4viously gave me 
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually)

just a thoery but could it down to me having bigger resalution (1280x1024) then what the games use to? i dunno just my theroy i doubt it is!

---

### Post by fblade1987 on 2006-08-16
OK just to let you know i managed to get bzflag working by isntalling xgl it all seems to be working now apart from im not able top use a few application or commands!

for example im no longer able to use 3ddesk, or aticontrol center but everything seems to run a lot smoother now! i also cant use the command glxinfo and fglxinfo what can i use instead of them

anyideas how i could get aticontrol working

---

### Post by geokok1981 on 2006-08-16
U got xgl??Man I envy you...still afraid to try...
I believe (but once more DO search for other posts to verify) that 
somethings dont work yet when you have xgl.
Regarding the commands u mentioned, again I think that xgl is a seperate and different displaying module therefore these commands that refer to the default one wont work.....I think.....

---

### Post by deathbyswiftwind on 2006-08-17
you need to reconfigure your xorg to use the fglrx driver as soon as you do that your set

---

