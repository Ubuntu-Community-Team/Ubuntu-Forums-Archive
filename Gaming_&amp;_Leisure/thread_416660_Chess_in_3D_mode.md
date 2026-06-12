---
title: "Chess in 3D mode"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by MiCovran on 2007-04-21
I just installed the new Feisty Fawn and I can't play chess in 3D because my "system does not have the required software to enable 3D mode".

What packages do I need to install?

Thanks.

---

### Post by blitzer on 2007-04-21
Hello,

Sounds like you need to install video card drivers (what video card do you have ?)  Try to include your system specs with posts for help, it makes helping easier :)

---

### Post by MiCovran on 2007-04-21
3D works on screensavers, so I don't think it's drivers. Here's the whole message:
```
Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.

You are still able to play chess in 2D without these packages.
```

---

### Post by Perfect Storm on 2007-04-21
Do you have python-opengl and libgtkglext1 installed?

---

### Post by toscy on 2007-04-21
> **MiCovran said:**
> 3D works on screensavers, so I don't think it's drivers. Here's the whole message:
```
Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.

You are still able to play chess in 2D without these packages.
```

The same thing happens to me and I have drivers installed.

---

### Post by MiCovran on 2007-04-21
> **Artificial Intelligence said:**
> Do you have python-opengl and libgtkglext1 installed?
Yes, I have tried that already.

---

### Post by blitzer on 2007-04-21
I suggest trying BrutalChess from the Add/Remove under Applications.  

> 3d chess with reflection of the chessmen
This is a 3d chess with reflection of the chessmen. It has got a
built-in ai player. The movements are animated.

This is really slow on my system until I tweek out Aiglx in my Xorg.  Default agp1x instead of 4x for my system really puts a dent in my gaming in Feisty.  Might have to go back to Edgy for my Video Card drivers to function for gaming.   :(

Still no mention of System specs. ?    If you say your drivers are set up correctly then my guess would be that the game is unfinished or files left out when packaging ?

---

### Post by chiefwhosm on 2007-04-21
I had the same problem when I tried, tracked down the makers website, and followed their apt-get package command. After that it worked for me:

apt-get install python2.4 python-gtk2 python-glade2

:)

---

### Post by Matthijs on 2007-04-22
```
apt-get install python2.4 python-gtk2 python-glade2
```
did not work for me.... nvidia driver installed..
I already had those packages..

---

### Post by Ahmed A. on 2007-04-22
I have the same problem, and I have those packages installed anyway.

---

### Post by DoktorSeven on 2007-04-22
For some reason the Python gtkglext package isn't available for Ubuntu through the package manager... go download and install  python-gtkglext1_1.1.0-2feisty_i386.deb from [here](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437) to fix (you'll also need the aforementioned python-opengl package, which IS available through the package manager...).

Worked for me.

---

### Post by Perfect Storm on 2007-04-22
> **DoktorSeven said:**
> For some reason the Python gtkglext package isn't available for Ubuntu through the package manager... go download and install  python-gtkglext1_1.1.0-2feisty_i386.deb from [here](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437) to fix (you'll also need the aforementioned python-opengl package, which IS available through the package manager...).

Worked for me.


But the game is? If so the people who (want to) play this game should bug report it.

---

### Post by olejorgen on 2007-04-24
> **DoktorSeven said:**
> For some reason the Python gtkglext package isn't available for Ubuntu through the package manager... go download and install  python-gtkglext1_1.1.0-2feisty_i386.deb from [here](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437) to fix (you'll also need the aforementioned python-opengl package, which IS available through the package manager...).

Worked for me.

Hm.. that does not work for me... :(

python-gtkglext1
python-opengl
is installed (not glade python2.4 etc. though)

---

### Post by cstudent on 2007-04-24
I used this how-to to get it working for me:

[http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/](http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/)

---

### Post by MiCovran on 2007-04-24
> **cstudent said:**
> I used this how-to to get it working for me:

[http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/](http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/)
Thanks a lot, cstudent. This is the only thing that worked for me.

---

### Post by olejorgen on 2007-04-24
eh... that was NOT worth it.. looked like **** (no offense).
Anyone know how to rotate?

---

### Post by DoktorSeven on 2007-04-24
No rotation or anything seems to be possible, just a bad perspective of the chessboard.

No 3d or anything, but I still like eboard as my GUI chess game of choice.

---

### Post by huzzak on 2007-04-24
Thanks cstudent.  That worked, though, as olejorgen said, it really isn't worth it.  Chintzy 3D that looks awful.  The 2D interface is much better looking.

---

### Post by YnHnMDx on 2007-04-26
I installed ubuntu feisty fawn from LiveCD. To enable 3D mode in chess I installed additional packages:

**1.** python-opengl_2.0.1.09.dfsg.1-0.3_i386.deb [http://packages.ubuntulinux.org/feisty/python/python-opengl](http://packages.ubuntulinux.org/feisty/python/python-opengl)

**2.** libgtkglext1_1.0.6-2.1ubuntu1_i386.deb [http://packages.ubuntulinux.org/feisty/libs/libgtkglext1](http://packages.ubuntulinux.org/feisty/libs/libgtkglext1)

**3.** python-gtkglext1_1.1.0-2feisty_i386.deb [http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437)

---

### Post by Ashrael on 2007-05-06
this one worked for me ;) on feisty...

[http://sourceforge.net/project/downloading.php?group_id=6348&use_mirror=mesh&filename=python-gtkglext1_1.1.0-2feisty_i386.deb&3735389](http://sourceforge.net/project/downloading.php?group_id=6348&use_mirror=mesh&filename=python-gtkglext1_1.1.0-2feisty_i386.deb&3735389)


grtz!

---

### Post by Lord Illidan on 2007-06-02
I expected much better than that tbh.. No rotation, no anti-aliasing, this does look like sh**.

---

### Post by RomeReactor on 2007-06-02
Hi people. As [blitzer]("http://ubuntuforums.org/showpost.php?p=2500029&postcount=7") already suggested, the alternative is to install BrutalChess, which looks a lot better, but the A.I. is very weak compared to glchess (plus they're working on very good looking [wooden textures]("http://brutalchess.sourceforge.net/") now).

*Wow. It seems like BrutalChess is all I talk about nowadays... Geez...

---

### Post by livearevolution on 2007-06-07
me too

Does anybody know the answer???  Help????:(

---

### Post by RomeReactor on 2007-06-07
HI livearevolution. If you mean the answer to enable the 3D aspect of the default chess game (glchess, part of gnome-games), then [DoktorSeven]("http://ubuntuforums.org/showpost.php?p=2510684&postcount=11") already answered that; it seems to be a bug, as [A.I. said]("http://ubuntuforums.org/showpost.php?p=2512910&postcount=12").

---

### Post by livearevolution on 2007-06-07
Thanks so much.  It worked perfect!!  Take care:KS:popcorn::KS:popcorn:

---

### Post by wilcan34 on 2007-06-27
Mikes page worked for me

---

### Post by orb9220 on 2007-06-27
Yep I also have been disappointed in any 3d chess for linux.

I assumed Linux=Geek=3d Chess. And there would be a slew of 3d chess for linux.
Boy was that stereotype blown away.

---

### Post by pavkb on 2007-07-12
Has the 3D glChess worked on a AMD64 version of Fiesty??

The GTKGLExt libs for python seem to be available only for i386
THanks

---

### Post by stchman on 2007-11-23
> **DoktorSeven said:**
> For some reason the Python gtkglext package isn't available for Ubuntu through the package manager... go download and install  python-gtkglext1_1.1.0-2feisty_i386.deb from [here](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437) to fix (you'll also need the aforementioned python-opengl package, which IS available through the package manager...).

Worked for me.

That worked exactly as it should.

---

### Post by go_beep_yourself on 2007-11-23
Can 3d chess be played over a network such as lan or internet?

---

### Post by stchman on 2007-11-24
I now have a procedure on my website that will allow you to install 3D support for glChess.

[http://www.stchman.com/glchess.html](http://www.stchman.com/glchess.html)

I hope this helps.

---

### Post by param22k on 2008-08-15
thanks a lot .... mike's page helped .. however, for hardy heron u don't need to download from the link thats mentioned ... u can install python-gtkglext1 (Ver: 1.1.0-3) from the package manager ... u also need the packages mentioned earlier in the topic ... i hope this makes sense.. :|

---

### Post by go_beep_yourself on 2008-08-16
Anybody want to play me a network game of 3d chess?

---

### Post by bamboomy on 2009-04-17
is python-gtkglext1 installed?

```

sudo apt-get install python-gtkglext1

```

S.

---

### Post by Dusal on 2009-06-05
Download, and installed from her:
[http://packages.ubuntu.com/jaunty/python-gtkglext1](http://packages.ubuntu.com/jaunty/python-gtkglext1)

---

### Post by jukzh on 2009-06-05
Hello All!
Who can say, what's going on my machine?
Chess fails to run :(
I find out 3 versions of python installed here.
So I try
```
$ python2.4 /usr/games/glchess 
Traceback (most recent call last):
  File "/usr/games/glchess", line 16, in ?
    import pygtk
ImportError: No module named pygtk

```and python2.5.4 and 2.6.2 outputs looks like same 
```

$ python2.5.4 /usr/games/glchess 
Failed to load GGZ config: 
Using OpenGL:
VENDOR=Mesa Project
RENDERER=Software Rasterizer
VERSION=2.1 Mesa 7.4
EXTENSIONS=GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_120 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_fragment_shader GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_program_debug GL_MESA_resize_buffers GL_MESA_texture_array GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_fragment_program GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGI_texture_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/glchess/gtkui/chessview.py", line 168, in __expose
    self.view.feedback.renderGL()
  File "/var/lib/python-support/python2.5/glchess/display.py", line 489, in renderGL
    self.scene.controller.render()
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/opengl.py", line 396, in render
    self.drawPieces()
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/opengl.py", line 897, in drawPieces
    piece.draw()
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/opengl.py", line 143, in draw
    self.chessSet.drawPiece(self.name, state, self.scene)
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/new_models.py", line 111, in drawPiece
    if glGetBoolean(GL_TEXTURE_2D):
  File "/usr/lib/python2.5/site-packages/OpenGL/wrapper.py", line 1631, in __call__
    return self.finalise()( *args, **named )
  File "/usr/lib/python2.5/site-packages/OpenGL/wrapper.py", line 683, in wrapperCall
    converter( pyArgs, index, self )
  File "/usr/lib/python2.5/site-packages/OpenGL/converters.py", line 195, in __call__
    return self.arrayType.zeros( self.getSize(pyArgs) )
  File "/usr/lib/python2.5/site-packages/OpenGL/arrays/arraydatatype.py", line 98, in zeros
    return cls.returnHandler().zeros( dims, typeCode or cls.typeConstant )
  File "/usr/lib/python2.5/site-packages/OpenGL/arrays/nones.py", line 32, in zeros
    raise TypeError( """Can't create NULL pointer filled with values""" )
TypeError: ("Can't create NULL pointer filled with values", 'Failure in cConverter <OpenGL.converters.SizedOutput object at 0x90b402c>', [GL_TEXTURE_2D], 1, <OpenGL.wrapper.glGetIntegerv object at 0x90b298c>)

sh: bug-buddy: not found

```Regards,
JK

---

### Post by xplinux557 on 2009-07-26
Hi

If you want 3D Chess to work, you should install
python-opengl and python-gtkglext packages.
Those are the two packages that fixed my problems
with 3D Chess. As for the libgtkglext1 package, it doesn't appear
to do anything, at least on my machine.

Reply if this fixed the problem :)

---

### Post by nadamsieee on 2009-11-26
Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/483947]("https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/483947")

---

