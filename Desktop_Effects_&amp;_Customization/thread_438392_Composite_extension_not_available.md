---
title: "Composite extension not available"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by stereo_sl on 2007-05-09
Hello!

When I try to start the Desktop Effects I get the message The Composite extension is not available. Also if I start beryl from the command line it fails with message: 
Checking for XComposite extension               : failed

I checked the package repository for keyword composite and found:
- libxcomposite1
- libxcb-composite0

...I have both installed, but I am not sure if Desktop-effects use this library.  Is there any other library I need to install?

I am not sure if this will help, but here is the timeline:
- when I installed Edubuntu Desktop Effects worked well
- then I installed Kubuntu-desktop
- then I removed Kubuntu-desktop - don't ask :KS 
- now I got this message

I have ATI Radeon 9550 graphic card.

Thanks in advance,
Z

---

### Post by Ateo on 2007-05-09
I'm pretty sure you need the following in xorg.conf even with ATI cards:```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Someone correct me if I'm wrong.

---

### Post by stereo_sl on 2007-05-10
Of, course...I overlooked that part in the xorg.conf, sory...
I did work...the GUI pops up, but when I click enable it says "Desktop effects could not be be enabled". Notice the be be...that's not a typo :)

Command line output is:
gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0

How do I install this GLX extension? Here is glxinfo...and this extension is missing

```
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
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
0x3c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

---

### Post by adieb on 2007-05-13
hey there, same problem to me. no glx extension....

i am looking around, if i find something i am going to write here

---

### Post by kpolice on 2007-05-13
You have a Radeon 9550 so your options are:

1) Use the open source driver (which I don't recommend)
2) Use the fglrx driver and install XGL

You should find a lot of tutorials here in the forums to set up on of the two or if you have time then try both.

```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

This won't work if you are using the fglrx driver. 

And I don't recommend the open source driver because:
1. it is slower
2. video quality is just awful
3. it doesn't support powerplay
4. it doesn't support acpi

---

### Post by celebrant on 2007-05-13
I have 9550 too and open source driver worked better for me. And it solved my "composite extension" problem. I suggest you to try it !

---

### Post by ivelasco on 2007-05-13
> **celebrant said:**
> I have 9550 too and open source driver worked better for me. And it solved my "composite extension" problem. I suggest you to try it !
  
Totally agree with you.
Beryl works so much better with the open source driver,but 3D perfomance is poor.You must decide what are you going to use more.i don't use games,for me the choice is clear,beryl works flawlessly with the radeon driver and almost out of the box.

---

### Post by kyousukun on 2007-05-21
im having the same problem too, ive set the last part or the xorg.config to

```
Section 
"Extensions"
	Option		"Composite"	"Enable"
EndSection
```

and it still doesn't work, uhm I'm still new to this ubuntu coding stuff and im trying to use compiz but my desktop effects keeps displaying > The Composite extension is not available
any help?
i've installed flgx or flgrx or whatever that is..
any help?:(

---

### Post by raist78 on 2007-05-21
What driver are you using? If you have a ATI card and you're using ATI proprietary drivers, then you just can't enable "composite" because the drivers don't support it. The only way you can use Desktop Effects while using proprietary drivers is XGL.
Instead, if you use open drivers, then you can enable "composite" anche Desktop Effects using AIGLX.

---

### Post by sfynx on 2007-05-22
Just a comment .. I am having the same problems with the T60 I use for work. It uses an ATI x1300 card. I've tried a number of the fixes listed here on the boards with no success. 

 I'm in the market to buy a new laptop for personal use and I can tell you I will not be buying another machine with an ATI card. My desktop machine has an ATI card and I've had similar issues.  I have never had these types of problems with nVidia.  Until ATI gets their act squared away with consistent open-source support for their cards, I'm not buying.

---

### Post by Cows on 2007-05-22
Make sure that you have the following enabled in the correct sections and you also have to have the correct librarys .. for me I have them by default. Im using Nvidia 7600 GS but it should work for ATI since it worked on edgy w/ my ATI Radeon 9200 PRO :) it's the same concept basically.

```
Section "Module"
	Load		"glx"
        Load		"vbe"
	Load		"dbi"
EndSection
```

```
Section "Device"
	Identifier	"Generic Video Card"
	#Driver		"nvidia" // this if for my nvidia card
        Driver           "ati" 
        # // ^^ the above should be for your ati card/driver. you might be using fglrx. if that is the                
        #case then it would be
        #Driver           "fglrx"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection
```

```
Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

---

### Post by biskut23 on 2007-07-12
Hey I just started using Ubuntu 7.04 feisty, and Im trying to get beryl/Desktop effects to work.

I have restricted drivers installed and It says that direct rendering is enabled, i dont know where to go next.

Thank you SOOO much for any help.  :)

---

### Post by tjpais on 2007-07-23
i am gettin the same error... i read somewhere in the posts that x1650 ati cards are not compatible with beryl and desktop effects...is this true?

this is wat i have

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6334 (8.34.8)

can anyone help me get my desktop effects on feisty to work?

---

### Post by s5demigh on 2007-07-25
I have an ATI Redeon X700 and I did everything right but Beryl just won't enable. I've tried just about every other way on this thread but nothing.

I'm semi new to ubuntu but I followed his tut:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

to install my video card. Then I followed his tut:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

to install beryl. I did everything but when I get to step 9:

Step 9 : Right click the diamond again. This time - select window manager - Beryl.

It will, what seems like, try to enable but it will go right back to the default setting. I'm not sure what to do. Any help will be great! Thanks in advance.

-Dennis

---

### Post by s5demigh on 2007-07-25
Anyone?:confused:

---

