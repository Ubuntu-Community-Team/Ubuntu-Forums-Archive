---
title: "VLC does not play .wmv - any ideas?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by bionnaki on 2006-08-09
VLC does not play the video from .wmv, only the audio. I have the w32 codecs installed. Any ideas on how I can correct this?

---

### Post by mlind on 2006-08-09
> **bionnaki said:**
> VLC does not play the video from .wmv, only the audio. I have the w32 codecs installed. Any ideas on how I can correct this?

Try installing vlc 0.8.5 .deb package for Ubuntu from VLC homepage. Make sure you've got the newest package of w32codecs too (w32codecs_20060611).
You may need ffmpeg aswell. With this setup, .wmv's should work.

---

### Post by anders_gud on 2006-08-09
> **bionnaki said:**
> VLC does not play the video from .wmv, only the audio. I have the w32 codecs installed. Any ideas on how I can correct this?

Native wmv9 support in ffmpeg now... Thanks Google Summer of Code!!!

Try this:

$ sudo apt-get install checkinstall libwxgtk2.6-dev libdvbpsi3-dev libmpeg2-4-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev gcc g++ automake1.9 autoconf libtool subversion cvs libx11-dev

mkdir ~/videolan

$ cd ~/videolan ; wget [http://downloads.videolan.org/pub/videolan/vlc/0.8.2/contrib/faad2-20040923.tar.bz2](http://downloads.videolan.org/pub/videolan/vlc/0.8.2/contrib/faad2-20040923.tar.bz2)
$ tar -jxvf faad2-20040923.tar.bz2 ; cd faad2-20040923
$ ./configure --prefix=/usr ; cd libfaad ; make

$ cd ~/videolan ; svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
$ cd ffmpeg ; ./configure --enable-pp --enable-gpl ; make

$ cd ~/videolan ; svn co svn://svn.videolan.org/vlc/trunk vlc-trunk
$ cd vlc-trunk ;

$ ./bootstrap ; ./configure --prefix=/usr --with-ffmpeg-tree=../ffmpeg --enable-faad --with-faad-tree=../faad2-20040923 --enable-esd --enable-alsa --enable-flac --enable-theora  --disable-hal --enable-v4l --enable-dvb --enable-dv
$ make ; sudo checkinstall

---

### Post by mlind on 2006-08-09
You can get up-to-date ffmpeg from Marillat's repository and vlc source package from Debian or Ubuntu repository. (Using checkinstall is bad..)

---

### Post by bionnaki on 2006-08-09
what is the source listing of the marillat's repo?

---

### Post by mlind on 2006-08-09
> **bionnaki said:**
> what is the source listing of the marillat's repo?

[http://www.debian-multimedia.org](http://www.debian-multimedia.org) should contain all the information you need. If you're about to recompile ffmpeg for your system, you'll need some extra dependencies and those can be found on same repository as ffmpeg source package.

---

### Post by anders_gud on 2006-08-09
> **mlind said:**
> (Using checkinstall is bad..)
yes you are right... quick hack.

wmv was enabled just the other day... if marillats source package isn't recent enough, try uncomment the wmv3 section in libavcodec/allcodecs.c.

---

### Post by mlind on 2006-08-09
> **anders_gud said:**
> yes you are right... quick hack.

wmv was enabled just the other day... if marillats source package isn't recent enough, try uncomment the wmv3 section in libavcodec/allcodecs.c.

Yeah, that should do it if I compile mplayer with latest ffmpeg from cvs. Thanks!

---

### Post by bionnaki on 2006-08-09
worked perfectly mlind. thanks.

---

### Post by OrganicPanda on 2006-08-12
ok i added the repository:

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sarge main

can someone please help me out with what i need to do to get wmv9 playing with video not just audio, theres a lot of names here like ffmpeg, videolan, mplayer etc.. what am i actually changing to get this to work? 

cheers

edit: 100 beans wooo

edit2: ok i just ran an update and that was busy doing its thing till it got to libmjpegtools0 when i got 

```

(Reading database ... 160042 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.3sarge1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.3sarge1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libmjpegtools-dev 1:1.8.0-0.0ubuntu1 (using .../libmjpegtools-dev_1%3a1.8.0-0.3sarge1_i386.deb) ...
Unpacking replacement libmjpegtools-dev ...
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.3sarge1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so i don't really know where i stand or how to get libmjpegtools0 working

---

### Post by Denta on 2006-08-15
> **anders_gud said:**
> Native wmv9 support in ffmpeg now... Thanks Google Summer of Code!!!
That sounds great!

I dont really understand all these word, is ffmpeg something that vlc uses to play video? Is it possible to watch wmv9 in vlc with correct install?

---

### Post by NTolerance on 2006-08-17
I've got WMV3s working in MPlayer, but not in Totem, Kaffeine, VLC, etc...

I don't like the MPlayer GUI, so how to do I get the other players to play these files?

---

