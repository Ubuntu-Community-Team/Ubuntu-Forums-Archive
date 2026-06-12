---
title: "Enemy Territory OpenGL Issues"
date: 2006-07-09
forum: Gaming &amp; Leisure
---

### Post by Joe S. on 2006-07-09
I open up the terminal, I put in sh et, and this is what happens.

[INDENT]shjoe@joe-desktop:~$ sh et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/joe/.etwolf/etmain
/home/joe/enemy-territory/etmain/pak2.pk3 (22 files)
/home/joe/enemy-territory/etmain/pak1.pk3 (10 files)
/home/joe/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/joe/enemy-territory/etmain/mp_bin.pk3 (6 files)
/home/joe/enemy-territory/etmain

----------------------
3763 files in pk3 files
^3WARNING: profile.pid found for profile 'Joe' - system settings will revert to defaults
execing default.cfg
couldn't exec language.cfg
execing profiles/Joe/etconfig.cfg
r_smp is unsafe. Check com_crashed.
r_mode is unsafe. Check com_crashed.
r_depthbits is unsafe. Check com_crashed.
r_stencilbits is unsafe. Check com_crashed.
r_stereo is unsafe. Check com_crashed.
r_colorbits is unsafe. Check com_crashed.
r_texturebits is unsafe. Check com_crashed.
r_clampToEdge is unsafe. Check com_crashed.
r_ext_texture_env_add is unsafe. Check com_crashed.
r_nv_fogdist_mode is unsafe. Check com_crashed.
r_ext_NV_fog_dist is unsafe. Check com_crashed.
r_ext_texture_filter_anisotropic is unsafe. Check com_crashed.
r_ati_fsaa_samples is unsafe. Check com_crashed.
r_ati_truform_pointmode is unsafe. Check com_crashed.
r_ati_truform_normalmode is unsafe. Check com_crashed.
r_ati_truform_tess is unsafe. Check com_crashed.
r_ext_ATI_pntriangles is unsafe. Check com_crashed.
r_glIgnoreWicked3D is unsafe. Check com_crashed.
r_ext_compiled_vertex_array is unsafe. Check com_crashed.
r_ext_multitexture is unsafe. Check com_crashed.
r_ext_gamma_control is unsafe. Check com_crashed.
r_ext_compressed_textures is unsafe. Check com_crashed.
r_allowExtensions is unsafe. Check com_crashed.
r_glDriver is unsafe. Check com_crashed.
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Received signal 11, exiting...
joe@joe-desktop:~$[/INDENT]

I've been able to run ET in software mode, but don't even get me started on how tormenting that is. I'm not really sure what's wrong with my ATI drivers for my 9600 SE, because I recalled installing them and have had OpenGL function just fine when playing CS 1.6.

I plug fglrxinfo into the terminal, and I get:

[INDENT]display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www*mesa3d*org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)[/INDENT]

I'm not even really sure what the problem is, well besides ET running terribly. Any helped be greatly appreciated.


not sure how to lock thread :x

---

### Post by Rackerz on 2006-07-09
The problem is your ATI driver didn't install correctly because it's still using the 'Mesa' OpenGL driver. I had this same problem, do you know what version of the ATI driver you installed?

---

### Post by Joe S. on 2006-07-09
Not exactly, I just followed [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").

---

### Post by Joe S. on 2006-07-09
Nevermind, apparently I didn't have all of the repositories I needed before. Now ET, TC:E, Warsow, and CS are all running smoother than ever. Thanks for helping me out about the drivers.

---

### Post by Rackerz on 2006-07-09
No problem, if you need anything just ask ;).

---

