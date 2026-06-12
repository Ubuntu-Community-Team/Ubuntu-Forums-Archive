---
title: "ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avformat_alloc_context"
date: 2009-02-28
forum: General Help
---

### Post by yilan198711 on 2009-02-28
when I use ffmpeg,it said that "ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avformat_alloc_context"

what can i do fot it ?

thank u ^^^

---

### Post by FakeOutdoorsman on 2009-02-28
I need more information to help you:
[list][*] What version of Ubuntu are you using?
[*] Is FFmpeg from the repository, or did you compile it yourself?
[*] Show your complete FFmpeg command and the complete FFmpeg output that generates this error.[/list]

---

### Post by motin on 2009-03-07
I get the same error in a debootstrap'd jaunty (using chroot) after the following commands:

```
--------------------- the latest x264 for ffmpeg
sudo apt-get install git
sudo apt-get install git-core
git clone git://git.videolan.org/x264.git
sudo sh configure --enable-shared --disable-asm
sudo make install

---------------------installing FFMPEG from subversion
sudo apt-get build-dep ffmpeg
sudo apt-get install libfaac-dev libfaad-dev libmp3lame-dev libxvidcore4-dev libavformat-dev libswscale-dev libavdevice-dev libavcodec-dev libavutil-dev
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
sudo sh configure --enable-libmp3lame --enable-libvorbis --enable-libxvid --enable-shared --enable-libfaac --enable-libfaad --enable-gpl --enable-libtheora --enable-libx264
sudo bash -c "echo '/usr/local/lib' >> /etc/ld.so.conf.d/custom-libs.conf"
sudo ldconfig
sudo make distclean
sudo checkinstall --pkgversion "`aptitude show ffmpeg | grep Version | awk '{print $2}'`-checkinstalled1"

```

ffmpeg svn rev is 17862.

The complete error:
```
# ffmpeg 
ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avformat_alloc_context
```

And through gdb:
```
root@motin-xps:/root/ffmpeg# gdb /usr/local/bin/ffmpeg
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) run
Starting program: /usr/local/bin/ffmpeg 
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
/usr/local/bin/ffmpeg: symbol lookup error: /usr/local/bin/ffmpeg: undefined symbol: avformat_alloc_context

Program exited with code 0177.
(gdb) 
```

I configured ffmpeg with --enabled-debug but still got the above, so I installed: sudo apt-get install libfaac0-dbgsym libfaad0-dbgsym lame-dbgsym libmpeg4ip-0-dbgsym libavformat52-dbgsym libswscale0-dbgsym libavdevice52-dbgsym libavcodec52-dbgsym libavutil49-dbgsym 

And instead I get:
```
root@motin-xps:/root/ffmpeg# gdb /usr/local/bin/ffmpeg
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) run
Starting program: /usr/local/bin/ffmpeg 
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
/usr/local/bin/ffmpeg: symbol lookup error: /usr/local/bin/ffmpeg: undefined symbol: avformat_alloc_context

Program exited with code 0177.
(gdb) 

```

Any ideas?

---

### Post by motin on 2009-03-08
Aha. Removing --enable-shared from the configure line solved it for me!

---

### Post by pelican69 on 2009-04-25
thanks for this important remark !!! I also had to remove "enable-shared" option. It works great now...
------------------------------------------
FFmpeg version SVN-r18693, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr/local --enable-gpl --enable-nonfree --enable-postproc --enable-avfilter --enable-avfilter-lavf --enable-pthreads --enable-x11grab --enable-bzlib --enable-libamr-nb --enable-libamr-wb --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libnut --enable-libschroedinger --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.27. 0 / 52.27. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 25 2009 16:46:03, gcc: 4.3.2

---

### Post by nschuil on 2009-04-29
Hello.

I get the same error:

root@server01:/usr/local/src/ffmpeg# ffmpeg
ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avformat_alloc_context

Everytime when using an 'own' compiled version of ffmpeg from the subversion archive (latest version).

I need the Shared modules, so i cant configure without --enable shared. Any idea how to resolve this problem?

---

### Post by FakeOutdoorsman on 2009-04-29
Compiled SVN FFmpeg with *--enabled-shared* seems to work fine for me with the limited tests I made.  I followed this guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Additional steps: Of course you need to add *--enabled-shared* to the FFmpeg configuration before compiling.  After installing FFmpeg, you will need to run:
```
sudo ldconfig
```

---

### Post by nealkrawetz on 2009-05-07
I just had the same problem.
I fixed it by removing other older versions of the libraries.

I had installed the new stuff (ffmpeg 0.5) in --prefix=/usr -- libraries in /usr/lib.
Turns out, I had some really old libraries in /usr/local/lib.
'sudo rm -rf /usr/local/lib/libav* ; sudo /sbin/ldconfig' removed the conflict. Now it works great.

---

### Post by monstrfolk on 2009-06-02
That's it. Cool, huh? Before you can start playing with your ffmpeg binary, you need to register those new dynamic libraries in /usr/local/lib (I'm using zsh. the syntax may be different if you're using another shell):

ubuntu% LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
ubuntu% export LD_LIBRARY_PATH
ubuntu% sudo ldconfig



from - [http://juliensimon.blogspot.com/2008/12/howto-compiling-ffmpeg-x264-mp3-xvid.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-ffmpeg-x264-mp3-xvid.html)

---

### Post by grahammills on 2009-06-29
Hi

I seem to have the same problem after using this guide with --enable-shared

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

It works fine without but need it for ffmpeg-php

I tried installing ffmpeg before finding this great guide using apt-get but with no success. So there might be some conflict because of this.

Any ideas, it's driving me nut trying to get it to work?

---

### Post by art2003 on 2009-10-13
instead of make install
type:

sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --default


that makes a .deb and installs it, it will tell you what files it conflicts with (and the library guilty of this)
apt-get remove those libraries and reinstall the .deb you created until it installs cleanly

then type ffmpeg

and it works (with shared enabled!!!!)

---

