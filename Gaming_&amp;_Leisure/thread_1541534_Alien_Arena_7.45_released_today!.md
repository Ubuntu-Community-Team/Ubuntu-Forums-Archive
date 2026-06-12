---
title: "Alien Arena 7.45 released today!"
date: 2010-07-29
forum: Gaming &amp; Leisure
---

### Post by Irritant on 2010-07-29
Official press release:

**A**lien Arena 2010 version 7.45 has been released today!

The latest edition of this open sourced, freeware FPS has been updated with a number of important improvements and bugfixes that not only enhance the visual appearance, but greatly improve the performance of the game.

Some of the new features include: 

[list]
[*]New Skeletal model format
[*]Soft shadows
[*]Faster, more accurate lighting 
[*]Major optimizations for faster rendering
[*]Fixes for older vertex animated models
[*]All player models re-animated with new model format
[*]A number of IRC client fixes
[*]Many model skins updated
[/list]
Alien Arena 2010(v7.45)

[[img]http://icculus.org/alienarena/rpa/mediathumbs/normalmap_m.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/normalmap.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/liquid_m.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/liquid.jpg)
[[img]http://icculus.org/alienarena/rpa/mediathumbs/softshadow_m.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/softshadow.jpg) [[img]http://icculus.org/alienarena/rpa/mediathumbs/purg_m.jpg[/img]](http://icculus.org/alienarena/rpa/mediathumbs/purg_big.jpg)

video - [http://www.youtube.com/watch?v=dgXCBpJT6H0](http://www.youtube.com/watch?v=dgXCBpJT6H0)

For a complete changelog - [http://icculus.org/alienarena/changelogs/7.45.txt](http://icculus.org/alienarena/changelogs/7.45.txt)

For more information, new media, and to download the game visit [http://red.planetarena.org](http://red.planetarena.org)

---

### Post by MaxIBoy on 2010-07-29
Ah, Irr beat me to it.

Anyway, the FPS boost really is non-trivial, thanks to optimizations in model rendering (newer maps use a lot of meshes.) In some cases, FPS are nearly doubling!

---

### Post by _h_ on 2010-07-29
Awesome. Downloaded the ZIP directly from atomicgamers, and hopefully PlayDeb updates their repos soon.

---

### Post by slooksterpsv on 2010-07-29
Downloading zip right now, I love this game =D

If you can't run the game on 64-bit, use this page to fix it:
[http://computergyan.wordpress.com/2010/05/09/fix-for-alien-arena-error-crx-error-while-loading-shared-libraries-libxxf86dga-so-1-in-ubuntu-10-0464bit/](http://computergyan.wordpress.com/2010/05/09/fix-for-alien-arena-error-crx-error-while-loading-shared-libraries-libxxf86dga-so-1-in-ubuntu-10-0464bit/)

---

### Post by 2Karl on 2010-07-29
This looks very nice from the videos. Can anyone tells me how it stacks up against something like say Nexuiz or Unreal Tournament?

---

### Post by MadBillyGoat on 2010-07-29
I also I downloaded the new version.
For some odd reason I am unable to get it to run at all.  
I download and installed the old version the easy way through the Software Center and it worked.
The read me states all i need to do is basicly cd to the drectory and ./crx  I did this and I get this message
 "[COLOR=Red]./crx: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by ./crx)[/COLOR]"
I tried to look up glbc_2.11 in synaptic and was unable to find something.
Does any one have any Idea?

Thanks

---

### Post by MaxIBoy on 2010-07-29
You probably need to recompile the game against your Glibc version. (I'm guessing you have an older version of Ubuntu, in which case PlayDeb is unlikely to package the latest AA for your distro.)

In the alien arena folder, try these commands:
```
sudo  apt-get install build-essential comerr-dev g++ gettext html2text  libaa1-dev libalut0 libasound2-dev libaudio-dev libaudio2  libaudiofile-dev libcaca-dev libcurl4-gnutls-dev libfreetype6-dev  libgcrypt11-dev libgl1-mesa-dev libglu1-mesa-dev libgnutls-dev  libgpg-error-dev libice-dev libidn11-dev libjpeg62-dev libkrb5-dev  libldap2-dev libopenal1\|openal-soft libopenal-dev libpng12-dev  libpthread-stubs0 libpthread-stubs0-dev libslang2-dev libsm-dev  libtasn1-3-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev  libxext-dev libxt-dev libxxf86dga-dev libxxf86vm-dev mesa-common-dev  sharutils tofrodos x11proto-core-dev x11proto-input-dev x11proto-kb-dev  x11proto-xext-dev x11proto-xf86dga-dev x11proto-xf86vidmode-dev  libvorbis\|libvorbis0a libvorbis-dev xtrans-dev zlib1g-dev
cd source
make clean
make
make install
```

That will install all dependencies and recompile CRX.

---

### Post by MadBillyGoat on 2010-07-29
Hello,
I am running 9.10,
I ran the sudo and then cd to the source of the arena game.. but I am unsure where to do the make clean, make, make install,
None of the commands worked in that source dir. where the game is located.
What dir. am I to be in.

I tried to run game anyway with out making -  I got the same message.

Thanks for the help.

---

### Post by MaxIBoy on 2010-07-29
Could you try running the make commands again, and copy-and-paste all error messages into a post so I can see what's going wrong? It's possible I'm not aware of a dependency or something... (In the terminal use control-shift-c instead of control-c for copying, as control-c already means "cancel.")

---

### Post by MadBillyGoat on 2010-07-29
nick@madbillygoat:~/Games/alienarena7_45$ sudo  apt-get install build-essential comerr-dev g++ gettext html2text  libaa1-dev libalut0 libasound2-dev libaudio-dev libaudio2  libaudiofile-dev libcaca-dev libcurl4-gnutls-dev libfreetype6-dev  libgcrypt11-dev libgl1-mesa-dev libglu1-mesa-dev libgnutls-dev  libgpg-error-dev libice-dev libidn11-dev libjpeg62-dev libkrb5-dev  libldap2-dev libopenal1\|openal-soft libopenal-dev libpng12-dev  libpthread-stubs0 libpthread-stubs0-dev libslang2-dev libsm-dev  libtasn1-3-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev  libxext-dev libxt-dev libxxf86dga-dev libxxf86vm-dev mesa-common-dev  sharutils tofrodos x11proto-core-dev x11proto-input-dev x11proto-kb-dev  x11proto-xext-dev x11proto-xf86dga-dev x11proto-xf86vidmode-dev  libvorbis\|libvorbis0a libvorbis-dev xtrans-dev zlib1g-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
comerr-dev is already the newest version.
g++ is already the newest version.
gettext is already the newest version.
html2text is already the newest version.
libaa1-dev is already the newest version.
libalut0 is already the newest version.
libasound2-dev is already the newest version.
libaudio-dev is already the newest version.
libaudio2 is already the newest version.
libaudiofile-dev is already the newest version.
libcaca-dev is already the newest version.
libcurl4-gnutls-dev is already the newest version.
libfreetype6-dev is already the newest version.
libgcrypt11-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
libglu1-mesa-dev is already the newest version.
libgnutls-dev is already the newest version.
libgpg-error-dev is already the newest version.
libice-dev is already the newest version.
libidn11-dev is already the newest version.
libjpeg62-dev is already the newest version.
libkrb5-dev is already the newest version.
libldap2-dev is already the newest version.
Note, selecting libopenal1 for regex 'libopenal1|openal-soft'
Note, selecting libopenal1-dbg for regex 'libopenal1|openal-soft'
libopenal-dev is already the newest version.
libpng12-dev is already the newest version.
libpthread-stubs0 is already the newest version.
libpthread-stubs0-dev is already the newest version.
libslang2-dev is already the newest version.
libsm-dev is already the newest version.
libtasn1-3-dev is already the newest version.
libx11-dev is already the newest version.
libxau-dev is already the newest version.
libxcb1-dev is already the newest version.
libxdmcp-dev is already the newest version.
libxext-dev is already the newest version.
libxt-dev is already the newest version.
libxxf86dga-dev is already the newest version.
libxxf86vm-dev is already the newest version.
mesa-common-dev is already the newest version.
sharutils is already the newest version.
tofrodos is already the newest version.
x11proto-core-dev is already the newest version.
x11proto-input-dev is already the newest version.
x11proto-kb-dev is already the newest version.
x11proto-xext-dev is already the newest version.
x11proto-xf86dga-dev is already the newest version.
x11proto-xf86vidmode-dev is already the newest version.
Note, selecting libvorbisfile-ruby for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbisfile-ruby1.8 for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbis-ocaml for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbisfile3 for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbisenc2 for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbisspi-java for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbis-ocaml-dev for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbis-perl for regex 'libvorbis|libvorbis0a'
Note, selecting libogg-vorbis-perl instead of libvorbis-perl
Note, selecting libvorbisidec1 for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbisidec-dev for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbis0a for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbis-dev for regex 'libvorbis|libvorbis0a'
Note, selecting libvorbis0 for regex 'libvorbis|libvorbis0a'
libvorbis-dev is already the newest version.
xtrans-dev is already the newest version.
zlib1g-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nick@madbillygoat:~/Games/alienarena7_45$ make clean
make: *** No rule to make target `clean'.  Stop.
nick@madbillygoat:~/Games/alienarena7_45$ make
make: *** No targets specified and no makefile found.  Stop.
nick@madbillygoat:~/Games/alienarena7_45$ make install
make: *** No rule to make target `install'.  Stop.
nick@madbillygoat:~/Games/alienarena7_45$ 


Ok I included the fist command you suggested. I've done similar things before.. I don't think I am in the correct dir. for all of this to work..

Thanks again ..  I hope you are a understanding person.

---

### Post by slooksterpsv on 2010-07-30
the make file is in alienarena7_45/source - try running it from there, but you shouldn't have to recompile it.

---

### Post by MadBillyGoat on 2010-07-30
Ya I found it and did it as you were posting I'm sure.  Sorry for my laziness,

Well I ran the commands and went to start the game ..  Here is what I got boss..

nick@madbillygoat:~/Games/alienarena7_45$ ./crx
using /home/nick/.codered/data1/ for writing
using /home/nick/.codered/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy

Ya bets me Im going looking for cfg's defalt and config  files.

Thanks

---

### Post by MaxIBoy on 2010-07-30
Okay, it seems that OpenAL is trying to use the OSS backend and that's not working. Try creating a file in your home folder called .alsoftrc (the dot at the beginning is important!) and put in these contents:
```
[general]
drivers=pulse
```If that doesn't work, try "alsa" or "port" instead of "pulse."

This forces OpenAL to use a different backend ("pulse" for PulseAudio, "port" for PortAudio, or "alsa" for ALSA.)

---

### Post by MadBillyGoat on 2010-07-30
Bingo,
I had to use the "port"
Ya I have a question..  Did this command change my global audio settings..

Thanks the title screen looks about ten billion times better the the old one I use to have.
I'm Going to mess with the game for a bit and hit the hay.. 
Thanks again.
MadBillyGoat - Plague

---

### Post by MaxIBoy on 2010-07-30
Nope, just the settings for programs that use OpenAL. OpenAL is used for 3D sound so it typically only gets used in games, and not for media players.

---

### Post by MadBillyGoat on 2010-07-30
Yup! That rocks.
Game looks great and single player is fun.. I need to just jump into the config and fix the binds..
Thank you for your help.

Madbillygoat

---

### Post by _h_ on 2010-07-30
I've informed PlayDeb about the AA update, and Mr. Christoph Korn said he would work on it this weekend to get it updated in the repos.

---

### Post by MaxIBoy on 2010-07-30
Sweet, thanks!

---

### Post by MadBillyGoat on 2010-07-30
HI again,
I have a silly problem, I've linked short cuts before, put the command in the panel or menu it really not hard it even will let you brows to if if your are really lazy.. For some reason It will Not work I have tried several ways.. I finally loaded it in terminal and this is what I got.
But get this It will only work in the dir of the game where the crx is located, I have even tried to copy crx to my desktop and run it.. It will not..  There is a link path I don't know how to do.  I know there is a link path or something that I am missing.  I do know where to even start to look for the answer.

nick@madbillygoat:~$ '/home/nick/Games/alienarena7_45/crx' 
using /home/nick/.codered/data1/ for writing
using /home/nick/.codered/arena/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
OpenAL Information:
Active Device: PortAudio Software
  Vendor:     OpenAL Community
  Version:    1.1 ALSOFT 1.8.466
  Renderer:   OpenAL Soft
  ALC Frequency: 44100
  Generated Buffer Count: 256
  ALC Mono Sources: 255
  ALC Stereo Sources: 1
  Generated Source Count: 128
Available Devices:
  PortAudio Software
------------------------------------
--------- [Loading Renderer] ---------
Master server at 174.37.203.131:27900
Sending shutdown to 174.37.203.131:27900
recursive shutdown
Error: Couldn't load pics/colormap.pcx
nick@madbillygoat:~$ '/home/nick/Games/alienarena7_45/./crx' 
using /home/nick/.codered/data1/ for writing
using /home/nick/.codered/arena/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
OpenAL Information:
Active Device: PortAudio Software
  Vendor:     OpenAL Community
  Version:    1.1 ALSOFT 1.8.466
  Renderer:   OpenAL Soft
  ALC Frequency: 44100
  Generated Buffer Count: 256
  ALC Mono Sources: 255
  ALC Stereo Sources: 1
  Generated Source Count: 128
Available Devices:
  PortAudio Software
------------------------------------
--------- [Loading Renderer] ---------
Master server at 174.37.203.131:27900
Sending shutdown to 174.37.203.131:27900
recursive shutdown
Error: Couldn't load pics/colormap.pcx
nick@madbillygoat:~$

---

### Post by Irritant on 2010-07-30
In the command, you need to have it cd to your alienarena7_45 folder before executing crx.

---

### Post by MadBillyGoat on 2010-07-30
Hello,
If I cd in the terminal it does work I explained it poorly.
In the "short-cut" that I enter I have these two lines in two different "short-cuts"

I tried to run the application using the " run in terminal option " but it closed too fast for me to copy and past anything.

First Short-cut

Name:
Command: home/nick/Games/alienarena7_45/crx

Second Short-cut

Name:
Command: home/nick/Games/alienarena7_45/./crx

neither of these short-cut will load the game

Thanks guys

---

### Post by Irritant on 2010-07-30
change the command to "cd home/nick/Games/alienarena7_45 ./crx"

---

### Post by MadBillyGoat on 2010-07-30
> **Irritant said:**
> change the command to "cd home/nick/Games/alienarena7_45 ./crx"


Hello,
 "I did this before but failed to state it."
When I do what is above I get this error:

Failed to execute child process "cd" (No such file or directory)

and this

Failed to execute child process "cd home/nick/Games/alienarena7_45 ./crx" (No such file or directory)

and when I use the simple Custom application launcher in the panel, and brows to the application it gives me this command in the line

/home/nick/Games/alienarena7_45/crx

Nothing happens here it just blinks :confused:

It seems that none of these thing want to work,  I have done this many times and never had any issues...  Hee I even tried to restart the system --  must have been a windows flashback for me..

Beets me it's just odd.

Thanks again,
Nick

---

### Post by MaxIBoy on 2010-07-30
That would be "cd home/nick/Games/alienarena7_45/; ./crx"
Irritant forgot the semicolon. (You could also hit enter for a line break between the commands.)

---

### Post by MadBillyGoat on 2010-07-30
> **MaxIBoy said:**
> That would be "cd home/nick/Games/alienarena7_45/; ./crx"
Irritant forgot the semicolon. (You could also hit enter for a line break between the commands.)

This command will only work in the Terminal.
I decided to through in a screen shot I hope it helps.

Thanks again and again.. :p

---

### Post by MaxIBoy on 2010-07-31
This solution may work for you:
[http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=5124](http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=5124)

---

### Post by rykel on 2010-08-03
> **_h_ said:**
> I've informed PlayDeb about the AA update, and Mr. Christoph Korn said he would work on it this weekend to get it updated in the repos.

Thank you so much! Alien Arena 7.45 is so talked about (especially the FPS thingy) that I cannot wait to try it out.

Speaking of .debs, see how late we Ubuntu people are to the Game... if Alien Arena and us had all supported Autopackage, we could have all got it on the very day AA released the new version.

And did anyone tell you that Autopackages can be installed as User, without messing with Root?   ):P

---

### Post by rykel on 2010-08-11
Well, still NO .deb on playdeb.net... disappointed.   :(

---

### Post by rykel on 2010-08-22
Hi people, NEWSFLASH!!!

Alien Arena 7.45 is now available for easy installation from PlayDeb.net!

Thanks to Joao of PlayDeb who took his precious time and effort to "deb" this wonderful game for us Ubuntu people.

---

### Post by s8dtvt on 2010-09-15
Today I just install Alien-arena 7.45 from getdeb.net. It run with sound and black screen, so I cann't play it. Please help me!!!

Here is output on terminal, thanks:

kod@king-of-dragon:~$ alien-arena
using /home/kod/.codered/data1/ for writing
using /home/kod/.codered/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
execing config.cfg
Console initialized.

------- sound initialization -------
OpenAL Information:
Active Device: PulseAudio Software
  Vendor:     OpenAL Community
  Version:    1.1 ALSOFT 1.12.854
  Renderer:   OpenAL Soft
  ALC Frequency: 44100
  Generated Buffer Count: 256
  ALC Mono Sources: 255
  ALC Stereo Sources: 1
  Generated Source Count: 128
Available Devices:
  PulseAudio Software
------------------------------------
--------- [Loading Renderer] ---------
Initializing OpenGL display
...setting mode 3: 1024 768
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 x86/MMX/SSE2
GL_VERSION: 2.1 Mesa 7.7.1
GL_EXTENSIONS: GL_EXT_compiled_vertex_array GL_EXT_texture_env_add GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_depth_clamp GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_seamless_cube_map GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_120 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_cull_vertex GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_blit GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_envmap_bumpmap GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_texture_signed_rgba GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_depth_clamp GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
...allowing CDS
...enabling GL_EXT_compiled_vertex_array
...ignoring GL_EXT_point_parameters
...3DFX_set_global_palette not found
...GL_EXT_shared_texture_palette not found
...using GL_ARB_multitexture
...GL_SGIS_multitexture not found
...using GL_ARB_texture_env_combine
...using GL_EXT_texture_filter_anisotropic
...using GL_EXT_stencil_wrap
...using GL_EXT_framebuffer_blit
...using GL_EXT_stencil_two_side
...using GL_ARB_vertex_buffer_object
...Initializing VBO cache
qglBlitFramebufferEXT not found...
------------------------------------
...Initializing IRC client
...IRC rejected due to unset player name
======== CRX Initialized ========

---

### Post by Irritant on 2010-09-15
What video card do you have?  Tungsten Graphics Inc?

---

### Post by Irritant on 2010-09-17
> **Siggibeer said:**
> can i get it for free somewhere?...and my second question is, is it available on german language? [-o<

Yes it is free [http://red.planetarena.org](http://red.planetarena.org) 

It is not in German however.

---

### Post by rykel on 2010-09-20
> **Siggibeer said:**
> can i get it for free somewhere?...and my second question is, is it available on german language? [-o<

If you are using Ubuntu, the best place to get Alien Arena is at [www.playdeb.net](www.playdeb.net). I believe the aliens speak either English or alienspeak, though, not German!   :)

---

### Post by s8dtvt on 2010-09-23
> **Irritant said:**
> What video card do you have?  Tungsten Graphics Inc?

I use VGA of Intel: Mobile 4 Series Chipset Integrated Graphics Controller. Thanks for reply
Here is output of "lspci".

kod@king-of-dragon:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

