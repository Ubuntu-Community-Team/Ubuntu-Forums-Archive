---
title: "svn ffmpeg problem"
date: 2010-01-10
forum: Desktop Environments
---

### Post by Mia1990 on 2010-01-10
I am trying to install ffmpeg from svn but i keep getting this error and i do not know what to do.
mia@mia:~/svn/ffmpeg$ ./configure --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libgsm --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl --enable-x11grab
libfaac is nonfree and --enable-nonfree is not specified.

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.
mia@mia:~/svn/ffmpeg$ 


Maybe install from source how would i do that?

---

### Post by FakeOutdoorsman on 2010-01-10
You're missing *--enable-nonfree* in your FFmpeg configuration line.  You might be interested in this step-by-step guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Mia1990 on 2010-01-10
Thank you i am still getting the a error from from ffmpeg i am trying to run todiscgui part of tovid the vhooks are crippled in ffmpeg so i am installing ffmpeg from subversion here is what i have done and the problems i have encountered along the way.I installed ffmpeg from subversion but i could not do it unless i took out these two options --enable-gpl --enable-x11grab then i was able to install it.The next error i received was
> todisc encountered an error:
Can't find ffmpeg's vhook's
Check the contents of /home/me/todisc.log to see what went wrong.
See the tovid website ([http://www.tovid.org](http://www.tovid.org)) for what to do next.
Sorry for the inconvenience!I know vhooks are broken and i think that has something to do with the option --enable-gpl --enable-x11grab that i could not install i guess my next question is how do i make them install or is there a better way of getting them.

---

### Post by Mia1990 on 2010-01-10
anyone???

---

### Post by FakeOutdoorsman on 2010-01-10
What version of Ubuntu are you using?  I'm not familiar with todisc or todiscgui, but **vhook** has been depreciated from FFmpeg SVN for at least six months I believe, but the FFmpeg 0.5 branch supports vhook.  The link above won't work for compiling 0.5 though, because FFmpeg 0.5 requires older packages and I'm unsure what versions will work for it.  Can you show the contents of */home/me/todisc.log*?

**Update:** Instead of compiling FFmpeg 0.5 and trying to figure out that mess, perhaps mc4man or another forum member can show you how to simply remove the *--disable-vhook* option from the official package and rebuild it.  I'm not really sure how to do that.  I do believe that vhook may want the **libimlib2-dev** package, so install that before rebuilding FFmpeg.

---

### Post by Mia1990 on 2010-01-10
Just upgraded to 9.10 karmic a few days ago sorry it still says 9.04 under my name.I have two logs in that dir,here is the todisc log

> you are using the following locale settings:
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
[todisc]: Creating pics directories...
[todisc]:
[todisc]: =========================================================
[todisc]:
[todisc]: Menu title: "My Video Collection"
[todisc]: (adjust with -menu-title)
[todisc]: Including the following videos:
[todisc]: Current font settings: 
[todisc]: -menu-font Helvetica
[todisc]: -menu-fontsize 30
[todisc]: -thumb-font Helvetica
[todisc]: -thumb-fontsize 20
[todisc]: Current menu settings: 
[todisc]: -menu-length 20 seconds
[todisc]:
[todisc]: =========================================================
[todisc]:
*******************************************************************************
todisc from the tovid suite - log for Sun Jan 10 03:41:43 EST 2010
*******************************************************************************


[todisc]: 
[todisc]: Creating a title image
Running convert -size 620x100 xc:none -font Helvetica -pointsize 30 -fill black 
-stroke black -gravity center -annotate +0+0 My Video Collection -fill #CDC0B0 
-stroke gray -strokewidth 1 -annotate +1+1 My Video Collection miff:- | convert 
- -trim +repage -blur 0x0.4 /tmp/todisc-work.1/title_txt.png
Running convert -size 620x300 xc:none -font Helvetica -pointsize 20 -fill black 
-stroke black -gravity west -annotate +0+0 caprica -fill #C6C6C6 -stroke gray 
-strokewidth 1 -annotate +1+1 caprica miff:- | convert - -trim +repage 
/tmp/todisc-work.1/thumb_title0.png
Running convert -size 620x300 xc:none -font Helvetica -pointsize 20 -fill black 
-stroke black -gravity west -annotate +0+0 caprica -fill #C6C6C6 -stroke gray 
-strokewidth 1 -annotate +1+1 caprica miff:- | convert - -trim +repage 
/tmp/todisc-work.1/thumb_title1.png

Running: ffmpeg -i 
/home/mia/Videos/Caprica.S01E00.EXTRAS.DVDRip.XviD-iNGOT/caprica.s01e00.video.blo
gs.the.birth.of.a.cylon.dvdrip.xvid-ingot.avi -ss 2 -s 384x256 -vframes 1 
-vcodec png -an -f rawvideo -y /tmp/todisc-work.1/showcase_img.png

FFmpeg version SVN-r21118, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Jan 10 2010 02:21:27 with gcc 4.4.1
  configuration: --enable-libmp3lame --enable-libtheora --enable-nonfree --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl
  libavutil     50. 7. 0 / 50. 7. 0
  libavcodec    52.46. 0 / 52.46. 0
  libavformat   52.46. 0 / 52.46. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 8. 0 /  0. 8. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mp3 @ 0xa52a0b0]Header missing
[NULL @ 0xa5296d0]Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from '/home/mia/Videos/Caprica.S01E00.EXTRAS.DVDRip.XviD-iNGOT/caprica.s01e00.video.blogs.the.birth.of.a.cylon.dvdrip.xvid-ingot.avi':
  Duration: 00:03:06.85, start: 0.000000, bitrate: 1403 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x400 [PAR 1:1 DAR 8:5], 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 32 kb/s
Output #0, rawvideo, to '/tmp/todisc-work.1/showcase_img.png':
    Stream #0.0: Video: png, rgb24, 384x256 [PAR 16:15 DAR 8:5], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[mpeg4 @ 0xa5296d0]Invalid and inefficient vfw-avi packed B frames detected
frame=    1 fps=  0 q=0.0 Lsize=     140kB time=0.03 bitrate=34406.6kbits/s    
video:140kB audio:0kB global headers:0kB muxing overhead 0.000000%
[todisc]: todisc encountered an error:
[todisc]: Can't find ffmpeg's vhook's
[todisc]: Cleaning up...
[todisc]: Removing /home/mia/todisc-work.1
[todisc]: Cleaning up...
[todisc]: Cleaning up...
[todisc]: Removing /home/mia/todisc-work.0Here is tovid/todiscgui [website]("http://tovid.wikia.com/wiki/Tovid_Wiki") if it helps you any
were could i download a older copy of ffmpeg at or are they broken in the rpm that fedora uses.I was thinking i could download a rpm of it and use alien to convert it to a deb?

---

### Post by SuperSonic4 on 2010-01-10
> **Mia1990 said:**
> Just upgraded to 9.10 karmic a few days ago sorry it still says 9.04 under my name.I have to logs in that dir,here is the todisc log



Here is tovid/todiscgui [website]("http://tovid.wikia.com/wiki/Tovid_Wiki") if it helps you any
were could i download a older copy of ffmpeg at or are they broken in the rpm that fedora uses.I was thinking i could download a rpm of it and use alien to convert it to a deb?

Can't you use the repo version if you'd like an old version? If you install SVN ffmpeg to /usr/local and put the following in ~/.bashrc ```
export PATH=/usr/local/bin:$PATH
```. You can then install repo ffmpeg together with svn version


If you still want to try SVN ffmpeg I'll paste my working config options below

```
./configure **--enable-pthreads** --enable-libx264 **--extra-cflags=-fPIC** --enable-libfaac --enable-libfaad --enable-encoder=x264 --enable-gpl --enable-nonfree *--enable-libopencore-amrnb* --enable-version3 --enable-encoder=libx264 --enable-encoder=h264 --enable-libvorbis --enable-libtheora --enable-libmp3lame --enable-libx264
```

You may not need the bits in bold if you run 32bit ubuntu. The part in italics is for AMR support

---

### Post by Mia1990 on 2010-01-10
vhooks are broken in the repo version tovid website says to install the svn version but i have had problems with that too the website says to do this
.> /configure --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libgsm --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl --enable-x11grab
but when i do it gives me a error so to fix that i have to remove  --enable-x11grab then it gives me a error and i have to remove --enable-gpl then it installs fine but tovid/todiscgui gives me a error ffmpeg can not find vhooks

---

### Post by mc4man on 2010-01-10
You should be ok if you build using FO's method but use the[ 0.5 release source]("http://ffmpeg.org/download.html")  instead.(bottom of  linked page

First remove the new x264 build you did
```
sudo apt-get remove x264
```

Then install karmic's libx264-67 and libx264-dev either from synaptic or 
```
sudo apt-get install libx264-67 libx264-dev
```

If you didn't dl the source from above link try something like this

```
mkdir ffmpeg1 && cd ffmpeg1
```
```
wget http://ffmpeg.org/releases/ffmpeg-0.5.tar.bz2
```
```
tar -xjvf ffmpeg-0.5.tar.bz2 && cd ffmpeg-0.5
```

```
./configure --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libgsm --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl --enable-nonfree --enable-x11grab


```

If you need swscale then add to the configure
--enable-swscale

Ex.

> doug@doug-laptop:~/ffmpeg8/ffmpeg-0.5$ ./configure --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libgsm --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl --enable-nonfree --enable-swscale
install prefix            /usr/local
source path               /home/doug/ffmpeg8/ffmpeg-0.5
C compiler                gcc
.align is power-of-two    no
ARCH                      x86 (generic)
big-endian                no
yasm                      yes
MMX enabled               yes
MMX2 enabled              yes
3DNow! enabled            yes
3DNow! extended enabled   yes
SSE enabled               yes
SSSE3 enabled             yes
CMOV enabled              no
CMOV is fast              no
EBX available             yes
EBP available             no
10 operands supported     yes
gprof enabled             no
debug symbols             yes
strip symbols             yes
optimizations             yes
static                    yes
shared                    no
postprocessing support    yes
software scaler enabled   yes
new filter support        no
filters using lavformat   no
[COLOR="Blue"]video hooking             yes[/COLOR]
Imlib2 support            yes
FreeType support          yes
network support           yes
IPv6 support              yes
threading support         pthreads
SDL support               yes
Sun medialib support      no
AVISynth enabled          no
libamr-nb support         no
libamr-wb support         no
libdc1394 support         no
libdirac enabled          no
libfaac enabled           yes
libfaad enabled           yes
libfaad dlopened          no
libgsm enabled            yes
libmp3lame enabled        yes
libnut enabled            no
libopenjpeg enabled       no
libschroedinger enabled   no
libspeex enabled          no
libtheora enabled         yes
libvorbis enabled         yes
libx264 enabled           yes
libxvid enabled           yes
vdpau enabled             no
zlib enabled              yes
bzlib enabled             yes


Build should proceed normally, ect.

Also don't know tovid at all but if if uses ffmpeg itself than you should be ok

---

### Post by Mia1990 on 2010-01-11
ffmpeg still cant find vhooks i installed ffmpeg from source i only had to take out --enable-libgsm this time so i am getting there  any help

---

### Post by FakeOutdoorsman on 2010-01-11
> **Mia1990 said:**
> ffmpeg still cant find vhooks i installed ffmpeg from source i only had to take out --enable-libgsm this time so i am getting there  any help

Show the output of: *ffmpeg -version*

---

### Post by mc4man on 2010-01-11
Just to add a little info
It certainly appears tovid (which is just a script), only needs ffmpeg itself, not the shared libs. ( so a static build should work

While I know nothing about vhook, it also appears using the 0.5 source and FO's guide does allow it's use.
[http://ubuntuforums.org/showthread.php?t=1153725&highlight=vhook](http://ubuntuforums.org/showthread.php?t=1153725&highlight=vhook)
Though again there was some add. info about .png's that's beyond me

---

### Post by Mia1990 on 2010-01-12
The repo's for some of the dependencies are not in ubuntu tovid website says
> For Ubuntu users for whom the apt-get build-dep does not work, I suggest you do a "apt-cache showsrc ffmpeg" and install the deps manually, getting the missing packages from another repository. ( for example libfaad-dev is apparently no longer in Ubuntu. ) 
I know i am doing the compiling like i should so my next question would be were do i get the repository's at or can i?

---

### Post by mc4man on 2010-01-12
That [wiki page ]("http://tovid.wikia.com/wiki/Installing_svn_ffmpeg_on_a_Debian_based_distro")you are reading is outdated and at this point, well, wrong. (it will not build a vhook enabled ffmpeg and you certainly don't want or need to add debian-multimedia to your sources.

Assuming that the recommended enables for ffmpeg are correct than if you follow as I posted they are the same ( and no need to remove remove libgsm from the configure if it's needed as is implied, though  I missed that you wanted x11grab - added to configure in previous post

run this to ck. on your dependencies
```
sudo apt-get install libmp3lame-dev libtheora-dev libx264-dev libgsm1-dev \
libxvidcore4-dev libvorbis-dev libfaad-dev libfaac-dev libsdl1.2-dev \
libx11-dev libxfixes-dev zlib1g-dev libimlib2-dev 

```
Then ```
sudo apt-get remove ffmpeg
```

And if you follow what I previously posted followed by a make and then use a checkinstall command of some sort, I guess this will do (not big on ck. install comm.'s
```
sudo checkinstall --pkgname=ffmpeg --pkgversion "5:0.5" --backup=no --deldesc=yes --delspec=yes --deldoc=yes --default
```

Then install tovid from synaptic and see...

> doug@doug-laptop:~$ ffmpeg
FFmpeg version 0.5, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libgsm --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl --enable-nonfree --enable-x11grab
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 12 2010 05:08:27, gcc: 4.4.1


---

### Post by Mia1990 on 2010-01-12
Thank you so much mc4man your my hero ffmpeg installed and is working great.I have not made a dvd yet but i ran todiscgui and i did not get any errors and it said something about found vhooks so i think it's going to work out great.

---

### Post by grepster on 2010-01-20
Just a suggestion that rather than struggling with vhooks you could just remove -quick-menu from your command line when using tovid/todisc (or just don't select it in todiscgui).  Then you would avoid the problem.  Processing will be much slower using imagemagick etc, but if you have a multi-core machine it will use all cpu's and that speeds things up quite a bit.  Also you will have access to fancy effects that need imagemagick like -rotate -wave -rotate-thumbs and others.

Apparently vhooks have been remove from current (svn) ffmpeg which is a shame as I don't think the new filters that replace it are mature enough to take over yet. (could be wrong there).  Maybe someday someone will update the todisc script to take advantage of the new filters. (libavfilter)

---

### Post by Mia1990 on 2010-01-20
My boyfriend and i have ffmpeg install and working great

---

