---
title: "Mplayer compiling error"
date: 2006-06-06
forum: Desktop Environments
---

### Post by shaul26 on 2006-06-06
I got it from the svn.. I ./configure it and them "make" but it gave me this error... whats wrong?

```

cc -I../libvo -I../../libvo  -fno-PIC -O4 -march=pentium4 -mtune=pentium4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I. -I/usr/include/     -I/usr/include/freetype2  -I/usr/include/SDL -D_REENTRANT    -I./libavutil -I./libavcodec   -o mplayer mplayer.o m_property.o mp_msg.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o m_config.o m_option.o m_struct.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subreader.o vobsub.o unrarlib.o mixer.o parser-mpcmd.o subopt-helper.o libvo/libvo.a libao2/libao2.a input/libinput.a  vidix/libvidix.a  libmpcodecs/libmpcodecs.a loader/libloader.a loader/dshow/libDS_Filter.a loader/dmo/libDMO_Filter.a libaf/libaf.a libmpdemux/libmpdemux.a postproc/libswscale.a osdep/libosdep.a -Llibmpdvdkit2 -lmpdvdkit libavcodec/libavcodec.a  libavformat/libavformat.a  libavutil/libavutil.a  libpostproc/libpostproc.a  -lmad -ldv -ltheora -logg     -lmp3lame   -ldts -lpng -lz -lz -ljpeg -lasound -ldl -lpthread  -lx264 -lpthread -lmpcdec   -lfaac -lfreetype -lz -lncurses  -lnsl       -lfontconfig   libfaad2/libfaad2.a  mp3lib/libMP3.a liba52/liba52.a libmpeg2/libmpeg2.a tremor/libvorbisidec.a  -laa -lGL -ldl  -lXv   -lXinerama -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread -lnsl -L/usr/lib -lSDL -lpthread      -L/usr/lib -lcaca -lslang -lX11 -L/usr/X11R6/lib -lncurses -lncurses   -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lesd -laudiofile -lm   -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl -lpthread    -Wl,-z,noexecstack     -lpthread -ldl -rdynamic  -lm
mplayer.o: In function `uninit_player':mplayer.c:(.text+0x3d5): undefined reference to `getch2_disable'
mplayer.o: In function `print_status':mplayer.c:(.text+0x995): undefined reference to `get_screen_size'
:mplayer.c:(.text+0x99b): undefined reference to `screen_width'
:mplayer.c:(.text+0xb9f): undefined reference to `erase_to_end_of_line'
:mplayer.c:(.text+0xced): undefined reference to `erase_to_end_of_line'
mplayer.o: In function `exit_sighandler':mplayer.c:(.text+0x2f88): undefined reference to `getch2_disable'
mplayer.o: In function `main':mplayer.c:(.text+0x929f): undefined reference to `getch2_enable'
:mplayer.c:(.text+0x9b5f): undefined reference to `load_termcap'
input/libinput.a(input.o): In function `mp_input_read_key_code':input.c:(.text+0xa18): undefined reference to `getch2'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

```

---

### Post by Sutekh on 2006-06-07
Is there a particular reason you want to compile mplayer? You can install it from the Ubuntu multiverse repository, which is far easier.


 Do you know how to add repositories?  If so you need to enable the **multiverse** repository.  
 
 If you don't know how to add the multiverse repository, here's how.
 
 First you need to backup and edit the file that contains the repository sources.
 ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list
 sudo gedit /etc/apt/sources.list
``` When the text editor opens you need to uncomment (remove the # sign) these lines
 ```
# deb http://archive.ubuntu.com/ubuntu breezy universe
 # deb-src http://archive.ubuntu.com/ubuntu breezy universe
 
 ...
 
 # deb http://security.ubuntu.com/ubuntu breezy-security universe
 # deb-src http://security.ubuntu.com/ubuntu breezy-security universe
``` and add **multiverse** to the end of them.
 
 They should look like this
 ```
deb http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
 deb-src http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
  
 ...
 
 deb http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
``` Save the file and then refresh the repositories list and then install mplayer using these commands
 ```
sudo apt-get update
 sudo apt-get install mplayer
``` 
Or open Synaptic (System -> Administration) and click Reload, and then Search for mplayer, mark it for installation and click Apply.

---

### Post by shaul26 on 2006-06-07
Hey :)
I want to compile mplayer because I heard that when compiling from svn the h264 is   much better...

do I need to remove my current mplayer to compile a new one?

---

### Post by mellon85 on 2006-06-07
Development version doesn't always compile, that's why releases exists.

---

### Post by shaul26 on 2006-06-07
So how can i get the latest version of mplayer?

---

### Post by mellon85 on 2006-06-07
these will build for sure
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

---

