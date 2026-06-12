---
title: "UFO: Alien Invasion 2.1 released!"
date: 2007-04-08
forum: Gaming &amp; Leisure
---

### Post by dolny on 2007-04-08
> The UFO:AI development team is proud to announce the release of UFO: Alien Invasion Version 2.1. This version features many great improvements over 2.0 and tons of new content, such as new aliens, new weapons, new maps, new base facilities, new research options and better multiplayer support. Many of the bugs that plagued version 2.0 have been eliminated.

[img]http://ufoai.ninex.info/gallery/cache/ingame-screenshots__crashsite.jpg_122.jpg[/img]

[img]http://ufoai.ninex.info/gallery/cache/ingame-screenshots__geoscape2.jpg_122.jpg[/img]

[img]http://ufoai.ninex.info/gallery/cache/ingame-screenshots__ingame009.jpg_122.jpg[/img]

You can get the debs here: [http://www.getdeb.net/](http://www.getdeb.net/) (scroll it a bit down)

...and the installer: [http://ufoai.ninex.info](http://ufoai.ninex.info) 

Join #ufo:ai on irc.freenode.de to get help and arrange multiplayer games.

This is my favourite open source game ever.

---

### Post by dolny on 2007-04-09
*bump* - weird, no comments on this great game?

---

### Post by Perfect Storm on 2007-04-09
Because it have already been announced: [http://gaming.gwos.org/comment.php?comment.news.23](http://gaming.gwos.org/comment.php?comment.news.23) back in 02 April ;)

---

### Post by hikaricore on 2007-04-09
And I posted it here on the forums as well.

[http://ubuntuforums.org/showthread.php?t=399257](http://ubuntuforums.org/showthread.php?t=399257)

Much better post than mine tho, I was tired that day. heh

---

### Post by dolny on 2007-04-10
Ah, sorry. Personally I've been using the unstable branch (2.2) of UFO and I switched to ArchLinux so I'm not visiting UbuntuForums as much as I used to. Anyway, try this game if you haven't :)

---

### Post by herot on 2007-04-11
Please help me install UFO:AI  i am running 6.06 dapper

i get 

andrew@andrew-desktop:~$ ufoai
./ufo: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by ./ufo)
andrew@andrew-desktop:~$

i tried installing some glibc packages through synaptic... couldn't get anything to work tho.  i also tried recompiling from source (show below):

root@andrew-desktop:/home/andrew/Desktop/ufoai-2.1-source# ./install-sh
./install-sh: no input file specified.
root@andrew-desktop:/home/andrew/Desktop/ufoai-2.1-source# ./install
bash: ./install: No such file or directory
root@andrew-desktop:/home/andrew/Desktop/ufoai-2.1-source# make install
make: *** No rule to make target `install'.  Stop.
root@andrew-desktop:/home/andrew/Desktop/ufoai-2.1-source# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for sed... yes
checking for echo... yes
checking target OS... linux-gnu
checking target CPU... i386
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for rm... yes
checking for mkdir... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdint.h... (cached) yes
checking stdint.h has intptr_t... yes
checking X11/Xlib.h usability... yes
checking X11/Xlib.h presence... yes
checking for X11/Xlib.h... yes
checking for library containing XCreateWindow... -lX11
checking for library containing dlopen... none required
checking for library containing cos... -lm
checking for library containing stricmp... no
checking for library containing strcasecmp... none required
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for library containing compress... -lz
checking for openal-config... no
configure: WARNING: cannot find openal-config might fail to find OpenAL!
checking AL/al.h usability... no
checking AL/al.h presence... no
checking for AL/al.h... no
checking AL/alc.h usability... no
checking AL/alc.h presence... no
checking for AL/alc.h... no
checking OpenAL/al.h usability... no
checking OpenAL/al.h presence... no
checking for OpenAL/al.h... no
checking OpenAL/alc.h usability... no
checking OpenAL/alc.h presence... no
checking for OpenAL/alc.h... no
checking for library containing ogg_stream_init... -logg
checking for library containing vorbis_info_init... -lvorbis
checking for library containing ov_open... -lvorbisfile
checking for library containing pthread_create... -lpthread
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for library containing gettext... none required
checking for sdl-config... yes
checking SDL.h usability... yes
checking SDL.h presence... yes
checking for SDL.h... yes
checking for library containing SDL_Init... -lSDL
checking for SDL_ttf.h... yes
checking for library containing TTF_Init... -lSDL_ttf
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for library containing jpeg_CreateDecompress... -ljpeg
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for library containing png_create_info_struct... -lpng
checking for GL/glx.h... yes
checking for glx.h... no
checking for library containing glXCreateContext... -lGL
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking OpenGL shader support... yes
checking jack/jack.h usability... no
checking jack/jack.h presence... no
checking for jack/jack.h... no
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking for library containing snd_pcm_open... none required
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking for artsc-config... yes
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking dsound.h usability... no
checking dsound.h presence... no
checking for dsound.h... no
checking for X11/extensions/xf86dga1.h... no
checking for X11/extensions/xf86dga.h... no
checking for X11/extensions/xf86vmode.h... no
configure: Without IPv6
configure: Enabling client
configure: Enabling dedicated server
configure: Enabling masterserver
configure: Enabling ufo2map
configure: Enabling qdata
configure: Enabling multilanguage support
configure: Enabling debug build
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
root@andrew-desktop:/home/andrew/Desktop/ufoai-2.1-source# make install
make: *** No rule to make target `install'.  Stop.
root@andrew-desktop:/home/andrew/Desktop/ufoai-2.1-source# make
CFLAGS
-----------------------
-g -O2 -D_GNU_SOURCE -D_BSD_SOURCE -D_XOPEN_SOURCE -std=c89 -DHAVE_CONFIG_H -Wall -pipe -DHAVE_SHADERS -ggdb -O0 -DDEBUG -fno-inline

LDFLAGS
-----------------------


Gettext
-----------------------
Type 'make lang' to compile the gettext translation files.
Type 'make update-po' to update with newest strings

Maps
-----------------------
Type 'make maps' to compile the maps

Built for debug-linux-gnu-i386

root@andrew-desktop:/home/andrew/Desktop/ufoai-2.1-source# make maps
make: *** base/maps: No such file or directory.  Stop.
make: *** [maps] Error 2
root@andrew-desktop:/home/andrew/Desktop/ufoai-2.1-source#

---

### Post by Perfect Storm on 2007-04-11
> ./ufo: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by ./ufo)

You need atleast Ubuntu 6.10 with the new UFO release, sorry.

---

### Post by FaceLeg on 2007-04-26
Hi,

After spending a full day attempting to install Half Life 2 (more for nostalgia's sake than anything else), I give up.

So I installed UFO:AI instead, and oh my goodness, this game is what I have been looking for!

I have one small problem though: neither by changing the vid_fullscreen "0/1" option, nor via the menu can I get UFO:AI to actually be "full s creen".  Both of the options set to full screen still leave me with a window.  

This game still rocks, however, and a trifling problem such as this will form now barrier to my play - it is just not as good as it could be.

Here is my config.cfg file:

```
// generated by ufo, do not modify
set ai_numactors "8"
set sv_teamplay "0"
set logstats "1"
set irc_logConsole "0"
set irc_password ""
set irc_user "UfoAIPlayer"
set irc_port "6667"
set irc_channel "#ufo:ai"
set irc_server "irc.freenode.org"
set msg "1"
set rate "25000"
set equip "multiplayer_initial"
set team "human"
set name "FaceLeg"
set mn_serverlist "0"
set mn_lastsave "slot0"
set mn_hud "hud"
set confirm_movement "0"
set confirm_actions "0"
set cl_start_buildings "1"
set cl_initial_equipment "human_phalanx_initial"
set cl_start_employees "1"
set cl_3dmap "0"
set cl_shownet "0"
set cl_fps "1"
set cl_aviMotionJpeg "1"
set cl_aviFrameRate "25"
set cl_aviForceDemo "1"
set cl_markactors "1"
set cl_mapzoommin "1.0"
set cl_mapzoommax "6.0"
set cl_centerview "1"
set cl_camzoomquant "0.16"
set cl_campitchspeed "0.5"
set cl_camyawspeed "160"
set cl_cammoveaccel "1250"
set cl_cammovespeed "750"
set cl_camrotaccel "400"
set cl_camrotspeed "250"
set cl_show_cursor_tooltips "1"
set cl_show_tooltips "1"
set cl_stereo_separation "0.4"
set adr15 ""
set adr14 ""
set adr13 ""
set adr12 ""
set adr11 ""
set adr10 ""
set adr9 ""
set adr8 ""
set adr7 ""
set adr6 ""
set adr5 ""
set adr4 ""
set adr3 ""
set adr2 ""
set adr1 ""
set adr0 ""
set cd_volume "1"
set cd_nocd "0"
set cursor "1"
set intensity "2"
set vid_grabmouse "1"
set gl_3dlabs_broken "1"
set gl_swapinterval "1"
set gl_ext_s3tc_compression "1"
set gl_ext_texture_compression "0"
set gl_ext_compiled_vertex_array "1"
set gl_ext_pointparameters "1"
set gl_ext_lockarrays "0"
set gl_ext_combine "1"
set gl_ext_multitexture "1"
set gl_ext_palettedtexture "1"
set gl_ext_swapinterval "1"
set gl_vertex_arrays "0"
set gl_showbox "0"
set gl_fog "1"
set gl_texturesolidmode "default"
set gl_texturealphamode "default"
set gl_texturemode "GL_LINEAR_MIPMAP_NEAREST"
set gl_driver "libGL.so.1"
set gl_finish "1"
set gl_maxtexres "2048"
set gl_imagefilter "1"
set gl_drawclouds "0"
set gl_stencil_two_side "1"
set gl_ati_separate_stencil "0"
set gl_shadow_debug_shade "0"
set gl_shadow_debug_volume "0"
set gl_shadows "1"
set gl_bitdepth "0"
set gl_modulate "1"
set gl_particle_att_c "0.01"
set gl_particle_att_b "0.0"
set gl_particle_att_a "0.01"
set gl_particle_size "40"
set gl_particle_max_size "40"
set gl_particle_min_size "2"
set gl_screenshot_jpeg_quality "75"
set gl_screenshot "jpg"
set r_texture_lod "0"
set r_anisotropic "1"
set r_displayrefresh "0"
set r_isometric "0"
set sensitivity "2"
set in_dgamouse "0"
set in_mouse "1"
set vid_gamma "1"
set vid_ypos "22"
set vid_xpos "3"
set vid_ref "glx"
set snd_device "default"
set snd_channels "2"
set snd_bits "16"
set s_libdir ""
set snd_ref "sdl"
set snd_openal "0"
set snd_music_volume "0.09"
set snd_mixahead "0.2"
set snd_loadas8bit "0"
set snd_khz "48"
set snd_volume "0.20"
set snd_init "1"
set con_history "1"
set s_language "en_NZ.UTF-8"
set sv_reconnect_limit "3"
set maxsoldiersperplayer "8"
set maxsoldiers "4"
set sv_enablemorale "1"
set hostname "noname"
set masterserver_port "27900"
set masterserver_ip "195.136.48.62"
set teamnum "1"
set gametype "1on1"
set s_sleep "1"
set cl_showcoords "0"
set cl_precachemenus "1"
set vid_fullscreen "1"
set gl_mode "6"
set fs_usehomedir "1"
```

---

### Post by NewJack on 2007-04-29
Can anyone help me?

I downloaded the installer file from the website.  It says it installed successfully and that in order to run the game, just type ufoai in a terminal.  But, when I type ufoai, nothing happens.  Did I do something wrong?  Is there a better way to install this game?  I didn't see it in the repos at all.

Any help is appreciated.  I am a huge fan of the original XCom game and hope to get this working.

Thanks!!!

---

### Post by glotz on 2007-06-19
> **Artificial Intelligence said:**
> You need atleast Ubuntu 6.10 with the new UFO release, sorry.
Sounds a bit harsh, is it really this simple? No workarounds?

(I'm still on Dapper and would also like to run it, and wouldn't like to compile as it probably would take ages on my old box unless i have to)

---

### Post by trinaryouroboros on 2007-06-19
I have 64-bit Ubuntu Linux, Feisty Fawn

I installed this game using the linux_hotfix2.run file found here:

[http://sourceforge.net/project/showfiles.php?group_id=157793&package_id=194208](http://sourceforge.net/project/showfiles.php?group_id=157793&package_id=194208)

It was missing libraries and wouldn't load, so I got peeved and made a script that will install the necessary libraries to get the game working.

If you have 64-bit ubuntu and want to give the script a shot, here it is:

[http://box.wyrmscape.com/share/ufox64ubuntu.sh](http://box.wyrmscape.com/share/ufox64ubuntu.sh)

Let me know if you have any problems!

---

### Post by daigidan on 2007-06-23
As an alternative to the script posted here, another alternative (that I found easier) is to install the [getlibs script provided by Cappy]("http://ubuntuforums.org/showthread.php?mode=hybrid&t=474790"). Then, you can just do:

```

getlibs -32 libogg.so.0
getlibs -32 libvorbis.so.0
getlibs -32 libvorbisfile.so.3
getlibs -32 libSDL_ttf-2.0.so.0

```

This worked like a charm for me. :]

---

### Post by Cappy on 2007-06-24
```
getlibs /usr/share/games/ufoai/ufo
```
works best since it will solve any dependencies you might be missing
 but
```
getlibs -32 libogg.so.0 libvorbis.so.0 libvorbisfile.so.3 libSDL_ttf-2.0.so.0
```
works too.

---

### Post by daigidan on 2007-06-24
I had tried:

```
getlibs /usr/local/games/ufoai/ufoai
```

But I always got:

```
This application isn't missing any dependencies!
```

ldd reports that ufoai is not a dynamic executable, which explains the above, but it's still extremely odd to me. I've been happily playing the game all weekend, however, so I'm not complaining. Thanks for a great script, I hope it makes its way into the main distribution.

---

### Post by searayman on 2007-06-25
When I try and run it i get this:

mike@mike-desktop:~$ ufoai
Killed
mike@mike-desktop:~$ 



any ideas?

---

### Post by hikaricore on 2007-06-25
> **searayman said:**
> When I try and run it i get this:

mike@mike-desktop:~$ ufoai
Killed
mike@mike-desktop:~$ 



any ideas?

I used to get the same thing.

It ended up having to do with my colour depth and possibly my video card.  >.<

What kinda hardware you got?

---

### Post by searayman on 2007-06-25
> **hikaricore said:**
> I used to get the same thing.

It ended up having to do with my colour depth and possibly my video card.  >.<

What kinda hardware you got?

Nvidia GeForce2 MX/MX 400

---

