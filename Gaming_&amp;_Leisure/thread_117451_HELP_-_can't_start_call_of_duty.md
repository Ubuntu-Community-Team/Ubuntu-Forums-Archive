---
title: "HELP - can't start call of duty"
date: 2006-01-14
forum: Gaming &amp; Leisure
---

### Post by theOrange on 2006-01-14
When i try to start call of duty using wine (installed with loki installer) it fails with this message:

X Error of failed request: GLXUnsupportedPrivateRequest
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 17 (X_GLXVendorPrivateWithReply)
Serial number of failed request: 1371
Current serial number in output stream: 1371

I am running breezy on a thinkpad t42 with a radeon 7500 mobile. I have just finished tweaking the xorg.conf/driconf and now get about 1500 fps after only getting 250. However i can't start COD

I'm using the DRI/radeon driver included with breezy. I also have wine 0.9.3.

Any ideas???

---

### Post by Mr_Grieves on 2006-01-14
First off, upgrade to Wine 0.9.5.

---

### Post by theOrange on 2006-01-14
[QUOTE=Mr_Grieves]First off, upgrade to Wine 0.9.5.[/QUOTE]

I would like to but 0.9.5 doesn't work as well in MeetingMaker and it's a work machine first. :(

This shouldn't matter should it? On wineHQ it says COD went gold with .9. 

Any specific reason to upgrade wine?

---

### Post by Mr_Grieves on 2006-01-14
Well, I don't keep track on all the changes they make in every release.. so I'm having a hard time to argue why not to upgrade beside that it might solve you're problem, hehe.

I guess you could try 0.9.5 and if there is no diffrence, you could downgrade to 0.9.3.

I search the net and found a Cedega/CoD howto.. if you can call it that.
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=52](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=52)

Else from that.. and the obvious google/winehq searches.. 
Make sure you CD to the binary first, and second do a 'wine game.exe'.

---

### Post by theOrange on 2006-01-14
[QUOTE=Mr_Grieves]Well, I don't keep track on all the changes they make in every release.. so I'm having a hard time to argue why not to upgrade beside that it might solve you're problem, hehe.

I guess you could try 0.9.5 and if there is no diffrence, you could downgrade to 0.9.3.

I search the net and found a Cedega/CoD howto.. if you can call it that.
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=52](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=52)

Else from that.. and the obvious google/winehq searches.. 
Make sure you CD to the binary first, and second do a 'wine game.exe'.[/QUOTE]

Thanks. All i can find on google so far has to do with the way the dri/radeon driver return the glx version string.  I think it is return 1.2 while it expects 1.3 even though it seems the driver supports the 1.3 extension anyway.

At least this is what i can find so far from this google search...

[http://www.mail-archive.com/wine-devel@winehq.org/msg23098.html](http://www.mail-archive.com/wine-devel@winehq.org/msg23098.html)

---

### Post by Mr_Grieves on 2006-01-14
I found this.. suggesting it would be a texture rending bug..
[http://www.mail-archive.com/flightgear-devel@flightgear.org/msg36910.html](http://www.mail-archive.com/flightgear-devel@flightgear.org/msg36910.html)

Abit of a clue perhaps:
[http://appdb.winehq.org/admin/adminTestResults.php?sub=view&iTestingId=683](http://appdb.winehq.org/admin/adminTestResults.php?sub=view&iTestingId=683)

and this.. from: [http://www.winehq.org/hypermail/wine-devel/2005.08.txt](http://www.winehq.org/hypermail/wine-devel/2005.08.txt)
Search on "GLXUnsupportedPrivateRequest" on that page..

> 
I downloaded a trial version of a Japanese RPG (Vagrants from Studio 
e.go, at [http://210.138.120.57/download/extra/vagrants_trial.exe)](http://210.138.120.57/download/extra/vagrants_trial.exe)), and 
tried to run it under Wine. This is a self-extracting archive, and it 
decompresses correctly, but when the main executable (vagrants.exe) is 
run, I get the following error:

trace:d3d:IWineD3DDeviceImpl_ActiveRender making new buffer
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  9274
  Current serial number in output stream:  9276

I could pinpoint the exact location of the call that fails. The line is 
dlls/wined3d/device.c, line 5592, at the call to glXMakeCurrent() in 
IWineD3DDeviceImpl_ActiveRender. But I am at a loss a how to fix this on 
my own. The function aborts the program instead of returning an error, 
as the code intends to check, so it cannot even recover from it. From 
what I googled, this seems to be some missing functionality of my X 
server (in Fedora 4), but there is no more information on how to fix 
this. Could somebody explain this error in more detail, and what can I 
do to aid in diagnosing or fixing it?

Using latest Wine CVS (at 2005/07/29).

Alex Villacis Lasso


and the answer:

> 
It looks like the X server you are using doesn't support the OpenGL related function
glXMakeCurrent(), can you send me the output of glxinfo?


---

### Post by theOrange on 2006-01-14
[QUOTE=Mr_Grieves]I found this.. suggesting it would be a texture rending bug..
[http://www.mail-archive.com/flightgear-devel@flightgear.org/msg36910.html](http://www.mail-archive.com/flightgear-devel@flightgear.org/msg36910.html)

Abit of a clue perhaps:
[http://appdb.winehq.org/admin/adminTestResults.php?sub=view&iTestingId=683](http://appdb.winehq.org/admin/adminTestResults.php?sub=view&iTestingId=683)

and this.. from: [http://www.winehq.org/hypermail/wine-devel/2005.08.txt](http://www.winehq.org/hypermail/wine-devel/2005.08.txt)
Search on "GLXUnsupportedPrivateRequest" on that page..



and the answer:[/QUOTE]

Thanks for doing some googling. That seems to be close although the opcode my failure is 143:17 so i'm not sure it is rendering?

Arghhh! It took me all of last night to get my fps just up to 1500 - i'm not ready for wine debugging! LOL

---

### Post by theOrange on 2006-01-14
I upgraded to 0.9.5 and now i at least get an error message. It says my video card might not support features required for the game. I have a Radeon 7500 Mobility on a ThinkPad T42.
So my question is: can this card play COD or do i just not have it configured correctly?

Has anyone played COD with this card? I have heard people playing it with less so i think i might not have it configured correctly. 

Any help would be great!


COD 1.3 build win-x86 Mar  2 2004
----- FS_Startup -----
Current language: english
Current search path:
C:\Program Files\cod\main\pakb.pk3 (60 files)
C:\Program Files\cod\main\paka.pk3 (41 files)
C:\Program Files\cod\main\pak9.pk3 (149 files)
C:\Program Files\cod\main\pak8.pk3 (235 files)
C:\Program Files\cod\main\pak6.pk3 (3 files)
C:\Program Files\cod\main\pak5.pk3 (4858 files)
C:\Program Files\cod\main\pak4.pk3 (1668 files)
C:\Program Files\cod\main\pak3.pk3 (1992 files)
C:\Program Files\cod\main\pak2.pk3 (694 files)
C:\Program Files\cod\main\pak1.pk3 (2642 files)
C:\Program Files\cod\main\pak0.pk3 (12816 files)
C:\Program Files\cod/main
C:\Program Files\cod\main\localized_english_pak5.pk3 (46 files)
    localized assets pak file for english
C:\Program Files\cod\main\localized_english_pak3.pk3 (7 files)
    localized assets pak file for english
C:\Program Files\cod\main\localized_english_pak2.pk3 (9 files)
    localized assets pak file for english
C:\Program Files\cod\main\localized_english_pak1.pk3 (3736 files)
    localized assets pak file for english
C:\Program Files\cod\main\localized_english_pak0.pk3 (1204 files)
    localized assets pak file for english

File Handles:
----------------------
30160 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec config.cfg
couldn't exec autoexec.cfg
========= autoconfigure
configure.csv: using configuration 1200 cpu MHz 512 sys MB 64 vid MB
execing configure.cfg
fs_basepath is write protected.
fs_homepath is write protected.
Hunk_Clear: reset the hunk ok
...detecting CPU, found Intel Pentium III
Measured CPU speed is 1.70 GHz
System memory is 1012 MB (capped at 1 GB)
Video card memory is 64 MB
Streaming SIMD Extensions (SSE) supported

----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'c:\windows\system32\opengl32.dll' ): succeeded
...setting mode 4: 800 600 FS
...using colorbits of 32
...calling CDS: ok
...registered window class
...created window@0,0 (800x600)
Initializing OpenGL driver
...getting DC: succeeded
...GLW_ChoosePFD( 32, 24, 8 )
...15 PFDs found
...MCD acceleration found
...PIXELFORMAT 6 selected
...creating GL context: succeeded
...making context current: succeeded
Initializing OpenGL extensions

GL_VENDOR: Tungsten Graphics, Inc.
GL_RENDERER: Mesa DRI Radeon 20050528 AGP 4x NO-TCL
GL_VERSION: 1.2 Mesa 6.3.2
GL_EXTENSIONS:  GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
----- CL_Shutdown -----
RE_Shutdown( 1 )
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...deleting GL context: success
...releasing DC: success
...destroying window
...resetting display
...shutting down QGL
...unloading OpenGL DLL
-----------------------
Hunk_Clear: reset the hunk ok
Your video card appears to be missing one or more features required to run Call of Duty.

You should install the latest drivers for your video card, being sure to uninstall the old drivers first.  If you already have the latest drivers, you should completely uninstall the drivers and then reinstall them.  This fixes most problems.  If the game still doesn't work, it may be that your video card does not have the minimum features required.  Please check the readme for more information, including a list of supported video cards.

---

### Post by Mr_Grieves on 2006-01-15
Do you have the newest driver? My and friends experience is that ATIs Linux support is abit .. less good.

Some good ATI links that might help:

ATIs Linux driver: [http://www.ati.com/support/driver.html](http://www.ati.com/support/driver.html) 
Official ATI+Linux Howto: [http://www.rage3d.com/content/articles/atilinuxhowto/](http://www.rage3d.com/content/articles/atilinuxhowto/) 
Linux-Gamers ATI+Linux Howto: [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=22](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=22) 
Official ATI+Linux FAQ: [http://www.ati.com/products/catalyst/linux.html](http://www.ati.com/products/catalyst/linux.html) 
Official ATI+Linux forum: [http://www.rage3d.com/board/forumdisplay.php?f=61](http://www.rage3d.com/board/forumdisplay.php?f=61)

---

