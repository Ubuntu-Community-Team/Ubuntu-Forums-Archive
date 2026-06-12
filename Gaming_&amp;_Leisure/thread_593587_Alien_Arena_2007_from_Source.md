---
title: "Alien Arena 2007 from Source"
date: 2007-10-27
forum: Gaming &amp; Leisure
---

### Post by s_spiff on 2007-10-27
Hi,
Trying to compile Alien Arena 2007 from source, I got from SVN. I installed the dependencies mentioned here :
[http://corent.proboards42.com/index.cgi?board=aatech&action=display&thread=1183028015](http://corent.proboards42.com/index.cgi?board=aatech&action=display&thread=1183028015)

Yet I get an error when I try to 'make' the setup. 

Here's the error, including the installing of the dependencies :

```

spiff@spiffed:~/Setups/Games/alien/source$ sudo apt-get install libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev libsdl1.2-dev libxxf86dga-dev xorg-dev subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
The following packages were automatically installed and are no longer required:
  libavahi-qt3-1 libarts1c2a kdelibs4c2a libmysqlclient15off fftw3
  libglademm-2.4-1c2a libtunepimp5 libboost-iostreams1.34.1 liblualib50
  ruby1.8 python-qt3 ruby libopenexr2c2a libkonq4 python-sip4 kdebase-bin
  libifp4 libdbus-qt-1-1c2 kdesktop kdebase-kio-plugins libboost-regex1.34.1
  kdelibs-data liblua50 libruby1.8 libsexymm2 mysql-common libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdmx-dev libfontenc-dev libfs-dev libogg-dev libsdl-mixer1.2
  libsdl-ttf2.0-0 libsmpeg-dev libsmpeg0 libtiff4-dev libtiffxx0c2
  libvorbis-dev libxaw-headers libxaw7-dev libxevie-dev libxfont-dev
  libxkbfile-dev libxkbui-dev libxkbui1 libxmuu-dev libxpm-dev libxss-dev
  libxtrap-dev libxv-dev libxvmc-dev x11proto-bigreqs-dev x11proto-dmx-dev
  x11proto-evie-dev x11proto-fontcache-dev x11proto-fonts-dev x11proto-gl-dev
  x11proto-scrnsaver-dev x11proto-trap-dev x11proto-video-dev
  x11proto-xcmisc-dev x11proto-xf86bigfont-dev x11proto-xf86dga-dev
  x11proto-xf86dri-dev
Recommended packages:
  libasound2-dev libaa1-dev libartsc0-dev libdirectfb-dev libcaca-dev
  libcucul-dev
The following NEW packages will be installed:
  libdmx-dev libfontenc-dev libfs-dev libogg-dev libsdl-image1.2-dev
  libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-ttf2.0-0 libsdl-ttf2.0-dev
  libsdl1.2-dev libsmpeg-dev libsmpeg0 libtiff4-dev libtiffxx0c2 libvorbis-dev
  libxaw-headers libxaw7-dev libxevie-dev libxfont-dev libxkbfile-dev
  libxkbui-dev libxkbui1 libxmuu-dev libxpm-dev libxss-dev libxtrap-dev
  libxv-dev libxvmc-dev libxxf86dga-dev x11proto-bigreqs-dev x11proto-dmx-dev
  x11proto-evie-dev x11proto-fontcache-dev x11proto-fonts-dev x11proto-gl-dev
  x11proto-scrnsaver-dev x11proto-trap-dev x11proto-video-dev
  x11proto-xcmisc-dev x11proto-xf86bigfont-dev x11proto-xf86dga-dev
  x11proto-xf86dri-dev xorg-dev
0 upgraded, 43 newly installed, 0 to remove and 0 not upgraded.
Need to get 3747kB of archives.
After unpacking 17.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy/main x11proto-dmx-dev 1:2.2.2-4ubuntu1 [6706B]
Get:2 http://archive.ubuntu.com gutsy/main libdmx-dev 1:1.0.2-2build1 [34.0kB]
Get:3 http://archive.ubuntu.com gutsy/main libfontenc-dev 1:1.0.4-2 [21.5kB]   
Get:4 http://archive.ubuntu.com gutsy/main x11proto-fonts-dev 2.0.2-5ubuntu1 [12.2kB]
Get:5 http://archive.ubuntu.com gutsy/main libfs-dev 2:1.0.0-4ubuntu2 [31.8kB] 
Get:6 http://archive.ubuntu.com gutsy/main libxpm-dev 1:3.5.6-3 [45.3kB]       
Get:7 http://archive.ubuntu.com gutsy/main libxaw-headers 2:1.0.3-3ubuntu1 [69.2kB]
Get:8 http://archive.ubuntu.com gutsy/main x11proto-evie-dev 1:1.0.2-4ubuntu1 [4622B]
Get:9 http://archive.ubuntu.com gutsy/main libxevie-dev 1:1.0.2-2 [10.5kB]     
Get:10 http://archive.ubuntu.com gutsy/main libxfont-dev 1:1.3.0-0ubuntu1 [284kB]
Get:11 http://archive.ubuntu.com gutsy/main libxkbfile-dev 1:1.0.4-1 [90.6kB]  
Get:12 http://archive.ubuntu.com gutsy/main libxkbui1 1:1.0.2-2 [9244B]        
Get:13 http://archive.ubuntu.com gutsy/main libxkbui-dev 1:1.0.2-2 [9394B]     
Get:14 http://archive.ubuntu.com gutsy/main x11proto-scrnsaver-dev 1.1.0.0-1 [5204B]
Get:15 http://archive.ubuntu.com gutsy/main libxss-dev 1:1.1.2-1 [16.6kB]      
Get:16 http://archive.ubuntu.com gutsy/main x11proto-trap-dev 3.4.3-5ubuntu1 [16.2kB]
Get:17 http://archive.ubuntu.com gutsy/main libxtrap-dev 2:1.0.0-4build1 [18.7kB]
Get:18 http://archive.ubuntu.com gutsy/main x11proto-video-dev 2.2.2-4ubuntu1 [9838B]
Get:19 http://archive.ubuntu.com gutsy/main libxv-dev 2:1.0.3-1ubuntu1 [37.3kB]
Get:20 http://archive.ubuntu.com gutsy/main libxvmc-dev 2:1.0.4-2ubuntu1 [20.4kB]
Get:21 http://archive.ubuntu.com gutsy/main x11proto-xf86dga-dev 2.0.2-4ubuntu1 [7338B]
Get:22 http://archive.ubuntu.com gutsy/main libxxf86dga-dev 2:1.0.1-2 [18.0kB] 
Get:23 http://archive.ubuntu.com gutsy/main x11proto-bigreqs-dev 1:1.0.2-4ubuntu1 [3998B]
Get:24 http://archive.ubuntu.com gutsy/main x11proto-fontcache-dev 0.1.2-4ubuntu1 [4592B]
Get:25 http://archive.ubuntu.com gutsy/main x11proto-xcmisc-dev 1.1.2-4ubuntu1 [3726B]
Get:26 http://archive.ubuntu.com gutsy/main x11proto-xf86bigfont-dev 1.1.2-4ubuntu1 [4526B]
Get:27 http://archive.ubuntu.com gutsy/main x11proto-xf86dri-dev 2.0.3-4ubuntu1 [5796B]
Get:28 http://archive.ubuntu.com gutsy/main libogg-dev 1.1.3-2ubuntu2 [93.7kB] 
Get:29 http://archive.ubuntu.com gutsy/main libsdl1.2-dev 1.2.11-9ubuntu2 [859kB]
Get:30 http://archive.ubuntu.com gutsy/main libtiffxx0c2 3.8.2-7ubuntu2 [5032B]
Get:31 http://archive.ubuntu.com gutsy/main libtiff4-dev 3.8.2-7ubuntu2 [573kB]
Get:32 http://archive.ubuntu.com gutsy/main libsdl-image1.2-dev 1.2.5-3 [38.0kB]
Get:33 http://archive.ubuntu.com gutsy/main libsmpeg0 0.4.5+cvs20030824-2 [106kB]
Get:34 http://archive.ubuntu.com gutsy/main libsdl-mixer1.2 1.2.6-3 [145kB]    
Get:35 http://archive.ubuntu.com gutsy/main libvorbis-dev 1.2.0.dfsg-1 [475kB] 
Get:36 http://archive.ubuntu.com gutsy/main libsmpeg-dev 0.4.5+cvs20030824-2 [117kB]
Get:37 http://archive.ubuntu.com gutsy/main libsdl-mixer1.2-dev 1.2.6-3 [201kB]
Get:38 http://archive.ubuntu.com gutsy/main libsdl-ttf2.0-0 2.0.9-1 [16.4kB]   
Get:39 http://archive.ubuntu.com gutsy/main libsdl-ttf2.0-dev 2.0.9-1 [26.1kB] 
Get:40 http://archive.ubuntu.com gutsy/main libxaw7-dev 2:1.0.3-3ubuntu1 [246kB]
Get:41 http://archive.ubuntu.com gutsy/main libxmuu-dev 2:1.0.3-1ubuntu1 [13.1kB]
Get:42 http://archive.ubuntu.com gutsy/main x11proto-gl-dev 1.4.8-1 [30.9kB]   
Get:43 http://archive.ubuntu.com gutsy/main xorg-dev 1:7.2-5ubuntu13 [1414B]   
Fetched 3747kB in 22m30s (2775B/s)                                             
Extracting templates from packages: 100%
Selecting previously deselected package x11proto-dmx-dev.
(Reading database ... 110068 files and directories currently installed.)
Unpacking x11proto-dmx-dev (from .../x11proto-dmx-dev_1%3a2.2.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libdmx-dev.
Unpacking libdmx-dev (from .../libdmx-dev_1%3a1.0.2-2build1_amd64.deb) ...
Selecting previously deselected package libfontenc-dev.
Unpacking libfontenc-dev (from .../libfontenc-dev_1%3a1.0.4-2_amd64.deb) ...
Selecting previously deselected package x11proto-fonts-dev.
Unpacking x11proto-fonts-dev (from .../x11proto-fonts-dev_2.0.2-5ubuntu1_all.deb) ...
Selecting previously deselected package libfs-dev.
Unpacking libfs-dev (from .../libfs-dev_2%3a1.0.0-4ubuntu2_amd64.deb) ...
Selecting previously deselected package libxpm-dev.
Unpacking libxpm-dev (from .../libxpm-dev_1%3a3.5.6-3_amd64.deb) ...
Selecting previously deselected package libxaw-headers.
Unpacking libxaw-headers (from .../libxaw-headers_2%3a1.0.3-3ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-evie-dev.
Unpacking x11proto-evie-dev (from .../x11proto-evie-dev_1%3a1.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxevie-dev.
Unpacking libxevie-dev (from .../libxevie-dev_1%3a1.0.2-2_amd64.deb) ...
Selecting previously deselected package libxfont-dev.
Unpacking libxfont-dev (from .../libxfont-dev_1%3a1.3.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libxkbfile-dev.
Unpacking libxkbfile-dev (from .../libxkbfile-dev_1%3a1.0.4-1_amd64.deb) ...
Selecting previously deselected package libxkbui1.
Unpacking libxkbui1 (from .../libxkbui1_1%3a1.0.2-2_amd64.deb) ...
Selecting previously deselected package libxkbui-dev.
Unpacking libxkbui-dev (from .../libxkbui-dev_1%3a1.0.2-2_amd64.deb) ...
Selecting previously deselected package x11proto-scrnsaver-dev.
Unpacking x11proto-scrnsaver-dev (from .../x11proto-scrnsaver-dev_1.1.0.0-1_all.deb) ...
Selecting previously deselected package libxss-dev.
Unpacking libxss-dev (from .../libxss-dev_1%3a1.1.2-1_amd64.deb) ...
Selecting previously deselected package x11proto-trap-dev.
Unpacking x11proto-trap-dev (from .../x11proto-trap-dev_3.4.3-5ubuntu1_all.deb) ...
Selecting previously deselected package libxtrap-dev.
Unpacking libxtrap-dev (from .../libxtrap-dev_2%3a1.0.0-4build1_amd64.deb) ...
Selecting previously deselected package x11proto-video-dev.
Unpacking x11proto-video-dev (from .../x11proto-video-dev_2.2.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxv-dev.
Unpacking libxv-dev (from .../libxv-dev_2%3a1.0.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libxvmc-dev.
Unpacking libxvmc-dev (from .../libxvmc-dev_2%3a1.0.4-2ubuntu1_amd64.deb) ...
Selecting previously deselected package x11proto-xf86dga-dev.
Unpacking x11proto-xf86dga-dev (from .../x11proto-xf86dga-dev_2.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxxf86dga-dev.
Unpacking libxxf86dga-dev (from .../libxxf86dga-dev_2%3a1.0.1-2_amd64.deb) ...
Selecting previously deselected package x11proto-bigreqs-dev.
Unpacking x11proto-bigreqs-dev (from .../x11proto-bigreqs-dev_1%3a1.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-fontcache-dev.
Unpacking x11proto-fontcache-dev (from .../x11proto-fontcache-dev_0.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-xcmisc-dev.
Unpacking x11proto-xcmisc-dev (from .../x11proto-xcmisc-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-xf86bigfont-dev.
Unpacking x11proto-xf86bigfont-dev (from .../x11proto-xf86bigfont-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-xf86dri-dev.
Unpacking x11proto-xf86dri-dev (from .../x11proto-xf86dri-dev_2.0.3-4ubuntu1_all.deb) ...
Selecting previously deselected package libogg-dev.
Unpacking libogg-dev (from .../libogg-dev_1.1.3-2ubuntu2_amd64.deb) ...
Selecting previously deselected package libsdl1.2-dev.
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.11-9ubuntu2_amd64.deb) ...
Selecting previously deselected package libtiffxx0c2.
Unpacking libtiffxx0c2 (from .../libtiffxx0c2_3.8.2-7ubuntu2_amd64.deb) ...
Selecting previously deselected package libtiff4-dev.
Unpacking libtiff4-dev (from .../libtiff4-dev_3.8.2-7ubuntu2_amd64.deb) ...
Selecting previously deselected package libsdl-image1.2-dev.
Unpacking libsdl-image1.2-dev (from .../libsdl-image1.2-dev_1.2.5-3_amd64.deb) ...
Selecting previously deselected package libsmpeg0.
Unpacking libsmpeg0 (from .../libsmpeg0_0.4.5+cvs20030824-2_amd64.deb) ...
Selecting previously deselected package libsdl-mixer1.2.
Unpacking libsdl-mixer1.2 (from .../libsdl-mixer1.2_1.2.6-3_amd64.deb) ...
Selecting previously deselected package libvorbis-dev.
Unpacking libvorbis-dev (from .../libvorbis-dev_1.2.0.dfsg-1_amd64.deb) ...
Selecting previously deselected package libsmpeg-dev.
Unpacking libsmpeg-dev (from .../libsmpeg-dev_0.4.5+cvs20030824-2_amd64.deb) ...
Selecting previously deselected package libsdl-mixer1.2-dev.
Unpacking libsdl-mixer1.2-dev (from .../libsdl-mixer1.2-dev_1.2.6-3_amd64.deb) ...
Selecting previously deselected package libsdl-ttf2.0-0.
Unpacking libsdl-ttf2.0-0 (from .../libsdl-ttf2.0-0_2.0.9-1_amd64.deb) ...
Selecting previously deselected package libsdl-ttf2.0-dev.
Unpacking libsdl-ttf2.0-dev (from .../libsdl-ttf2.0-dev_2.0.9-1_amd64.deb) ...
Selecting previously deselected package libxaw7-dev.
Unpacking libxaw7-dev (from .../libxaw7-dev_2%3a1.0.3-3ubuntu1_amd64.deb) ...
Selecting previously deselected package libxmuu-dev.
Unpacking libxmuu-dev (from .../libxmuu-dev_2%3a1.0.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package x11proto-gl-dev.
Unpacking x11proto-gl-dev (from .../x11proto-gl-dev_1.4.8-1_all.deb) ...
Selecting previously deselected package xorg-dev.
Unpacking xorg-dev (from .../xorg-dev_1%3a7.2-5ubuntu13_all.deb) ...
Setting up x11proto-dmx-dev (1:2.2.2-4ubuntu1) ...
Setting up libdmx-dev (1:1.0.2-2build1) ...
Setting up libfontenc-dev (1:1.0.4-2) ...
Setting up x11proto-fonts-dev (2.0.2-5ubuntu1) ...
Setting up libfs-dev (2:1.0.0-4ubuntu2) ...
Setting up libxpm-dev (1:3.5.6-3) ...
Setting up libxaw-headers (2:1.0.3-3ubuntu1) ...
Setting up x11proto-evie-dev (1:1.0.2-4ubuntu1) ...
Setting up libxevie-dev (1:1.0.2-2) ...
Setting up libxfont-dev (1:1.3.0-0ubuntu1) ...
Setting up libxkbfile-dev (1:1.0.4-1) ...
Setting up libxkbui1 (1:1.0.2-2) ...

Setting up libxkbui-dev (1:1.0.2-2) ...
Setting up x11proto-scrnsaver-dev (1.1.0.0-1) ...
Setting up libxss-dev (1:1.1.2-1) ...
Setting up x11proto-trap-dev (3.4.3-5ubuntu1) ...
Setting up libxtrap-dev (2:1.0.0-4build1) ...
Setting up x11proto-video-dev (2.2.2-4ubuntu1) ...
Setting up libxv-dev (2:1.0.3-1ubuntu1) ...
Setting up libxvmc-dev (2:1.0.4-2ubuntu1) ...
Setting up x11proto-xf86dga-dev (2.0.2-4ubuntu1) ...
Setting up libxxf86dga-dev (2:1.0.1-2) ...
Setting up x11proto-bigreqs-dev (1:1.0.2-4ubuntu1) ...
Setting up x11proto-fontcache-dev (0.1.2-4ubuntu1) ...
Setting up x11proto-xcmisc-dev (1.1.2-4ubuntu1) ...
Setting up x11proto-xf86bigfont-dev (1.1.2-4ubuntu1) ...
Setting up x11proto-xf86dri-dev (2.0.3-4ubuntu1) ...
Setting up libogg-dev (1.1.3-2ubuntu2) ...
Setting up libsdl1.2-dev (1.2.11-9ubuntu2) ...

Setting up libtiffxx0c2 (3.8.2-7ubuntu2) ...

Setting up libtiff4-dev (3.8.2-7ubuntu2) ...

Setting up libsdl-image1.2-dev (1.2.5-3) ...
Setting up libsmpeg0 (0.4.5+cvs20030824-2) ...

Setting up libsdl-mixer1.2 (1.2.6-3) ...

Setting up libvorbis-dev (1.2.0.dfsg-1) ...
Setting up libsmpeg-dev (0.4.5+cvs20030824-2) ...
Setting up libsdl-mixer1.2-dev (1.2.6-3) ...
Setting up libsdl-ttf2.0-0 (2.0.9-1) ...

Setting up libsdl-ttf2.0-dev (2.0.9-1) ...
Setting up libxaw7-dev (2:1.0.3-3ubuntu1) ...
Setting up libxmuu-dev (2:1.0.3-1ubuntu1) ...
Setting up x11proto-gl-dev (1.4.8-1) ...
Setting up xorg-dev (1:7.2-5ubuntu13) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
spiff@spiffed:~/Setups/Games/alien/source$ make
make targets BUILDDIR=release CFLAGS=" -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -ftree-vectorize -fexpensive-optimizations -march=k8"
make[1]: Entering directory `/home/spiff/Setups/Games/alien/source'
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -ftree-vectorize -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/gl_glx.o -c unix/gl_glx.c
make[1]: curl-config: Command not found
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -ftree-vectorize -fexpensive-optimizations -march=k8 -o release/crx release/client/cl_cin.o release/client/cl_ents.o release/client/cl_fx.o release/client/cl_input.o release/client/cl_inv.o release/client/cl_main.o release/client/cl_newfx.o release/client/cl_parse.o release/client/cl_pred.o release/client/cl_tent.o release/client/cl_scrn.o release/client/cl_view.o release/client/cl_http.o release/client/console.o release/client/keys.o release/client/menu.o release/client/snd_dma.o release/client/snd_mem.o release/client/snd_mix.o release/client/qmenu.o release/client/cmd.o release/client/cmodel.o release/client/common.o release/client/crc.o release/client/cvar.o release/client/files.o release/client/mdfour.o release/client/net_chan.o release/client/sv_ccmds.o release/client/sv_ents.o release/client/sv_game.o release/client/sv_init.o release/client/sv_main.o release/client/sv_send.o release/client/sv_user.o release/client/sv_world.o release/client/q_shunix.o release/client/vid_menu.o release/client/vid_so.o release/client/sys_unix.o release/client/rw_unix.o release/client/glob.o release/client/net_udp.o release/client/q_shared.o release/client/pmove.o release/ref_gl/r_bloom.o release/ref_gl/r_draw.o release/ref_gl/r_image.o release/ref_gl/r_light.o release/ref_gl/r_main.o release/ref_gl/r_mesh.o release/ref_gl/r_misc.o release/ref_gl/r_model.o release/ref_gl/r_refl.o release/ref_gl/r_math.o release/ref_gl/r_script.o release/ref_gl/r_surf.o release/ref_gl/r_vlights.o release/ref_gl/r_warp.o release/ref_gl/qgl_unix.o release/client/snd_unix.o release/client/snd_mixa.o -lm -ldl  release/ref_gl/gl_glx.o -L/usr/X11R6/lib64 -L/usr/local/lib64 -lX11 -lXext -lXxf86dga -lXxf86vm -lm -ljpeg -lGL -lGLU  -ljpeg
release/client/cl_http.o: In function `CL_InitHttpDownload':
cl_http.c:(.text+0x55): undefined reference to `curl_multi_init'
cl_http.c:(.text+0x66): undefined reference to `curl_easy_init'
release/client/cl_http.o: In function `CL_HttpDownloadCleanup':
cl_http.c:(.text+0xaf): undefined reference to `curl_multi_remove_handle'
release/client/cl_http.o: In function `CL_ShutdownHttpDownload':
cl_http.c:(.text+0x191): undefined reference to `curl_easy_cleanup'
cl_http.c:(.text+0x1a8): undefined reference to `curl_multi_cleanup'
release/client/cl_http.o: In function `CL_HttpDownloadThink':
cl_http.c:(.text+0x1eb): undefined reference to `curl_multi_perform'
cl_http.c:(.text+0x211): undefined reference to `curl_multi_info_read'
cl_http.c:(.text+0x24d): undefined reference to `curl_easy_getinfo'
release/client/cl_http.o: In function `CL_HttpDownload':
cl_http.c:(.text+0x395): undefined reference to `curl_easy_reset'
cl_http.c:(.text+0x3ad): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x3c5): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x3ee): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x406): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x419): undefined reference to `curl_multi_add_handle'
collect2: ld returned 1 exit status
make[1]: *** [release/crx] Error 1
make[1]: Leaving directory `/home/spiff/Setups/Games/alien/source'
make: *** [build-release] Error 2
spiff@spiffed:~/Setups/Games/alien/source$ sudo apt-get install libsdl-mixer1.2-dev libsdl-image1.2-dev libsdl-ttf2.0-dev libsdl1.2-dev libxxf86dga-dev xorg-dev subversion
[sudo] password for spiff:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl-mixer1.2-dev is already the newest version.
libsdl-image1.2-dev is already the newest version.
libsdl-ttf2.0-dev is already the newest version.
libsdl1.2-dev is already the newest version.
libsdl1.2-dev set to manual installed.
libxxf86dga-dev is already the newest version.
xorg-dev is already the newest version.
subversion is already the newest version.
The following packages were automatically installed and are no longer required:
  libavahi-qt3-1 libarts1c2a kdelibs4c2a libmysqlclient15off fftw3
  libglademm-2.4-1c2a libtunepimp5 libboost-iostreams1.34.1 liblualib50
  ruby1.8 python-qt3 ruby libopenexr2c2a libkonq4 python-sip4 kdebase-bin
  libifp4 libdbus-qt-1-1c2 kdesktop kdebase-kio-plugins libboost-regex1.34.1
  kdelibs-data liblua50 libruby1.8 libsexymm2 mysql-common libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
spiff@spiffed:~/Setups/Games/alien/source$ make
make targets BUILDDIR=release CFLAGS=" -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -ftree-vectorize -fexpensive-optimizations -march=k8"
make[1]: curl-config: Command not found
make[1]: Entering directory `/home/spiff/Setups/Games/alien/source'
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -ftree-vectorize -fexpensive-optimizations -march=k8 -o release/crx release/client/cl_cin.o release/client/cl_ents.o release/client/cl_fx.o release/client/cl_input.o release/client/cl_inv.o release/client/cl_main.o release/client/cl_newfx.o release/client/cl_parse.o release/client/cl_pred.o release/client/cl_tent.o release/client/cl_scrn.o release/client/cl_view.o release/client/cl_http.o release/client/console.o release/client/keys.o release/client/menu.o release/client/snd_dma.o release/client/snd_mem.o release/client/snd_mix.o release/client/qmenu.o release/client/cmd.o release/client/cmodel.o release/client/common.o release/client/crc.o release/client/cvar.o release/client/files.o release/client/mdfour.o release/client/net_chan.o release/client/sv_ccmds.o release/client/sv_ents.o release/client/sv_game.o release/client/sv_init.o release/client/sv_main.o release/client/sv_send.o release/client/sv_user.o release/client/sv_world.o release/client/q_shunix.o release/client/vid_menu.o release/client/vid_so.o release/client/sys_unix.o release/client/rw_unix.o release/client/glob.o release/client/net_udp.o release/client/q_shared.o release/client/pmove.o release/ref_gl/r_bloom.o release/ref_gl/r_draw.o release/ref_gl/r_image.o release/ref_gl/r_light.o release/ref_gl/r_main.o release/ref_gl/r_mesh.o release/ref_gl/r_misc.o release/ref_gl/r_model.o release/ref_gl/r_refl.o release/ref_gl/r_math.o release/ref_gl/r_script.o release/ref_gl/r_surf.o release/ref_gl/r_vlights.o release/ref_gl/r_warp.o release/ref_gl/qgl_unix.o release/client/snd_unix.o release/client/snd_mixa.o -lm -ldl  release/ref_gl/gl_glx.o -L/usr/X11R6/lib64 -L/usr/local/lib64 -lX11 -lXext -lXxf86dga -lXxf86vm -lm -ljpeg -lGL -lGLU  -ljpeg
release/client/cl_http.o: In function `CL_InitHttpDownload':
cl_http.c:(.text+0x55): undefined reference to `curl_multi_init'
cl_http.c:(.text+0x66): undefined reference to `curl_easy_init'
release/client/cl_http.o: In function `CL_HttpDownloadCleanup':
cl_http.c:(.text+0xaf): undefined reference to `curl_multi_remove_handle'
release/client/cl_http.o: In function `CL_ShutdownHttpDownload':
cl_http.c:(.text+0x191): undefined reference to `curl_easy_cleanup'
cl_http.c:(.text+0x1a8): undefined reference to `curl_multi_cleanup'
release/client/cl_http.o: In function `CL_HttpDownloadThink':
cl_http.c:(.text+0x1eb): undefined reference to `curl_multi_perform'
cl_http.c:(.text+0x211): undefined reference to `curl_multi_info_read'
cl_http.c:(.text+0x24d): undefined reference to `curl_easy_getinfo'
release/client/cl_http.o: In function `CL_HttpDownload':
cl_http.c:(.text+0x395): undefined reference to `curl_easy_reset'
cl_http.c:(.text+0x3ad): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x3c5): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x3ee): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x406): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x419): undefined reference to `curl_multi_add_handle'
collect2: ld returned 1 exit status
make[1]: *** [release/crx] Error 1
make[1]: Leaving directory `/home/spiff/Setups/Games/alien/source'
make: *** [build-release] Error 2
spiff@spiffed:~/Setups/Games/alien/source$ 


```

If someone can help me out with whats the error ?

---

### Post by fain on 2007-10-27
looks like you need libcurl


```

make[1]: curl-config: Command not found
```

---

### Post by DahVid on 2007-10-27
You also need libcurl development libraries (sorry, don't use ubuntu - don't know the exact name.)

---

### Post by fain on 2007-10-27
this should probably do it
```
sudo apt-get install libcurl3 libcurl3-dev
```

---

### Post by s_spiff on 2007-10-27
rocking. got  them on synaptic. its installed, now hoping it'll work :D

---

### Post by fain on 2007-10-27
rofl i just read your sig spiff thats good stuff

---

### Post by s_spiff on 2007-10-28
Thanks for your help guys.. Worked fine now. Its a little too fast for my taste, and as of yet, I haven't been able to exactly add more bots in the single player mode, but oh well, if not WOP, atleast this worked :D

---

