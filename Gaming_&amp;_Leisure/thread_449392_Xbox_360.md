---
title: "Xbox 360"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by keepthereceipt on 2007-05-20
Okay so I haven bailed on m$ fully yet, but Im wondering if there are any good apps to stream video to my 360.  Also perhaps some other Xbox 360 friendly apps would be cool.  How many ubuntu users have Xbox 360&#347;?  


Thanks =D
KeepTheReceipt

---

### Post by safullblown on 2007-05-29
Yeah try this [http://ushare.geexbox.org/](http://ushare.geexbox.org/)

---

### Post by keepthereceipt on 2007-05-31
I just got redirected to my original post from another hahah....thanks dude

---

### Post by brandon079 on 2007-10-08
I do. This would be nice but I tried tutorial and I think may be just over my head. Hopefully a gui version comes out soon,

---

### Post by Octagonal on 2007-10-20
I've tried ushare out for a couple weeks now.
Works on both Feisty and Gutsy.  I was only able to get wmv movies to play though I didn't try too hard w/ avi files or mpegs.  One problem is that if you are skipping chapters in the wmv the video will crap out and dump you to the 360's dashboard.

I just tried Twonky media server and this plays HD WMVs and searches wmv files just fine--I will have to try the other supported media files like mp4 and avi.  

So far Twonky seems to be better but it's got a 30 day trial before you should pay...

I've tried fuppes, which is supposed to offer some experimental transcoding but I have yet to get this working--my xbox 360 sees it but doesn't display any of the movies, pictures or music.

now to figure out how to get MKV->WMVs...

---

### Post by Octagonal on 2007-10-22
scratch my previous post, once fuppes is setup it works better than twonky and ushare.  Twonky seems a little flaky when trying to detect it on my xbox--basically worked the first time then I could only connect to it about 25% of my attempts.

Fuppes was the most difficult to setup but once that was done it plays movies better than ushare (as the chapter searching was flawless so far w/ fuppes).  Also the time or duration of each movie was represented properly in every case with fuppes (not so w/ twonky).

By the way if you are setting up fuppes and you can connect but it can't see your videos...
>  You have to edit the vfolder.cfg and change the node: 
 
<vfolder name="Folders" id="21" /> 
 
in the xbox layout to: 
 
<vfolder name="Folders" id="21"> 
<folders filter="contains(videoItem)" /> 
</vfolder>


this info was received from [http://sourceforge.net/forum/forum.php?thread_id=1834858&forum_id=475749](http://sourceforge.net/forum/forum.php?thread_id=1834858&forum_id=475749)
which resolved my problem connecting.

---

### Post by tomjennings83 on 2007-10-22
why would you want to stream videos to your xbox 360?

---

### Post by Sockerdrickan on 2007-10-22
HDTV maybe :popcorn:

---

### Post by stuart.crouch on 2007-10-22
An xbox 360 is usually plugged into a TV (in a lounge/bedroom)
A PC is usually sat in an office.

If you stream from the office to an xbox, you can watch movies and stuff in your lounge/bedroom without moving the PC!  

Sit in a sofa or sit at your computer desk watching it on a monitor... I know what I'd choose.

---

### Post by Octagonal on 2007-10-22
> **tomjennings83 said:**
> why would you want to stream videos to your xbox 360?

If you have HD movies on your computer how else would you get HD content to your HDTV.  Streaming to your xbox obviates the need for an HDDVD/Bluray player.

---

### Post by SBFC on 2007-10-31
> scratch my previous post, once fuppes is setup it works better 

You just followed the instructions and changed the appropriate places in fuppes.cfg & vfolder.cfg?

I followed the instructions for the 360 at the wiki: [http://fuppes.ulrich-voelkel.de/wiki/index.php/Microsoft_Xbox_360]("http://fuppes.ulrich-voelkel.de/wiki/index.php/Microsoft_Xbox_360")
and I´m having no luck at all.

Xbox just won´t see anything...can´t figure what I´m doing wrong.

---

### Post by Octagonal on 2007-11-04
Yes, just followed the instructions on the wiki as you listed... aside from the instructions the only thing I could add would be to make sure, if you're running firestarter, to allow the xbox to communicate w/ the xbox's IP address.

---

### Post by UofLSpeed on 2007-11-05
I've got FUPPES working, but video quality is less than perfect and the audio will not stay synced.  Playing on my desktop shows no problems with the file.

Anyone have any tips such as bitrates or codecs that worked for them?  Otherwise it looks like my 360 is only useful to stream music.

Aside from the games of course.

---

### Post by lime4x4 on 2007-11-06
I got fuppes installed and my xbox360 c's my linux box but it can't find any of the music. i have the folder listed in fuppes is there anything else i have to do?

---

### Post by Octagonal on 2007-11-06
is XBOX 360 support enabled in your vfolder.cfg file?

there should be a line that looks like:
> 
  <vfolder_layout device="Xbox 360" enabled="true">


---

### Post by lime4x4 on 2007-11-07
below is a copy of my file. The location of music on my pc is /media/sdc1/music/albums

&#8722;
	<fuppes_vfolder_config version="0.2">
&#8722;
	<vfolder_layout device="default" enabled="false">
&#8722;
	<vfolder name="Genre">
&#8722;
	<vfolders property="genre">
<items type="audioItem"/>
</vfolders>
</vfolder>
&#8722;
	<vfolder name="Genre/Artists">
&#8722;
	<vfolders property="genre">
&#8722;
	<vfolders property="artist">
<items type="audioItem"/>
</vfolders>
</vfolders>
</vfolder>
&#8722;
	<vfolder name="Artists/Albums">
&#8722;
	<vfolders property="artist">
&#8722;
	<vfolders property="album">
<items type="audioItem"/>
</vfolders>
</vfolders>
</vfolder>
&#8722;
	<vfolder name="ABC/Artists/Albums">
&#8722;
	<vfolders split="ABC">
&#8722;
	<vfolders property="artist">
&#8722;
	<vfolders property="album">
<items type="audioItem"/>
</vfolders>
</vfolders>
</vfolders>
</vfolder>
&#8722;
	<vfolder name="Photos">
&#8722;
	<vfolder name="All">
<items type="imageItem"/>
</vfolder>
&#8722;
	<vfolder name="Folders">
<folders filter="contains(imageItem)"/>
</vfolder>
</vfolder>
&#8722;
	<vfolder name="Videos">
&#8722;
	<vfolder name="All">
<items type="videoItem"/>
</vfolder>
&#8722;
	<vfolder name="Folders">
<folders filter="contains(videoItem)"/>
</vfolder>
</vfolder>
&#8722;
	<vfolder name="shared dirs">
<shared_dirs full_extend="true"/>
</vfolder>
</vfolder_layout>
&#8722;
	<vfolder_layout device="Xbox 360" enabled="true">
&#8722;
	<vfolder name="Music" id="1">
&#8722;
	<vfolder name="Album" id="7">
&#8722;
	<vfolders property="album" type="container.album.musicAlbum">
<items type="audioItem"/>
</vfolders>
</vfolder>
&#8722;
	<vfolder name="All Music" id="4">
<items type="audioItem"/>
</vfolder>
&#8722;
	<vfolder name="Artist" id="6">
&#8722;
	<vfolders property="artist" type="container.person.musicArtist">
<items type="audioItem"/>
</vfolders>
</vfolder>
&#8722;
	<vfolder name="Folders" id="20">
<folders filter="contains(audioItem)"/>
</vfolder>
&#8722;
	<vfolder name="Genre" id="5">
&#8722;
	<vfolders property="genre" type="container.genre.musicGenre">
<items type="audioItem"/>
</vfolders>
</vfolder>
<vfolder name="Playlist" id="15"/>
</vfolder>
&#8722;
	<vfolder name="Pictures" id="3">
<vfolder name="Album" id="13"/>
&#8722;
	<vfolder name="All Pictures" id="11">
<items type="imageItem"/>
</vfolder>
<vfolder name="Date Taken" id="12"/>
&#8722;
	<vfolder name="Folders" id="22">
<folders filter="contains(imageItem)"/>
</vfolder>
</vfolder>
&#8722;
	<vfolder name="Playlists" id="18">
<vfolder name="All Playlists" id="19"/>
<vfolder name="Folders" id="23"/>
</vfolder>
&#8722;
	<vfolder name="Video" id="2">
&#8722;
	<vfolder name="Actor" id="10">
<folders filter="contains(videoItem)"/>
</vfolder>
<vfolder name="Album" id="14"/>
&#8722;
	<vfolder name="All Video" id="8">
<items type="videoItem"/>
</vfolder>
&#8722;
	<vfolder name="Folders" id="21">
<folders filter="contains(videoItem)"/>
</vfolder>
<vfolder name="Genre" id="9"/>
</vfolder>
</vfolder_layout>
</fuppes_vfolder_config>

---

### Post by Octagonal on 2007-11-07
I've attached copies of my fuppes.cfg and vfolder.cfg files for comparison.
My NIC uses eth0 and I've set the IP address for my xbox along w/ nailing down the port to use.

I would suggest trying one mp3 in one folder first to start just to make sure there is not anything else potentially causing the problem.

Once you edit the fuppes.cfg and vfolder.cfg files in the fuppes terminal window:
r  [enter]         #to rebuild the database then
v  [enter]        #to rebuild the virtual folder layout

So it looks like:


> 
new device: Xbox 360 :: MediaRenderer
new UPnP device:
Xbox 360 (MediaRenderer)
r
[ContentDatabase] create database at Wed Nov  7 17:04:06 2007
read shared directories
[DONE] read shared directories
parse playlists
[DONE] parse playlists
parse iTunes databases
[DONE] parse iTunes databases
[ContentDatabase] database created at Wed Nov  7 17:04:11 2007
v
[VirtualContainer] create virtual container layout started at Wed Nov  7 17:04:13 2007
[VirtualContainer] virtual container layout created at Wed Nov  7 17:04:13 2007



---

### Post by lime4x4 on 2007-11-07
tried that no luck either here is a partial copy of my .cfg file

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/media/sdc1/music/albums</dir>-->
  </shared_objects>
  <network>
    <interface>eth1</interface>
    <ip_address>192.168.1.101</ip_address>
    <http_port>5000</http_port>
  </network>

---

### Post by Octagonal on 2007-11-07
> 
<!--<dir>/media/sdc1/music/albums</dir>-->


should be changed to:
> 
<dir>/media/sdc1/music/albums</dir>


the <!-- comments out that xml line.

---

### Post by lime4x4 on 2007-11-07
Ok that fixed some of my problems.Now i can see my songs but can't play them. When i try to play them fuppes quits with this error

john@john-feisty:~$ fuppes
            FUPPES - SVN-r551
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

new device: WRT54G :: unknown
new UPnP device:
WRT54G (unknown)
new device: WRT54G :: unknown
new UPnP device:
WRT54G (unknown)
new device: WRT54G :: unknown
new UPnP device:
WRT54G (unknown)
webinterface: [http://192.168.1.101:5000](http://192.168.1.101:5000)

r = rebuild database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

:1: parser warning : xmlns:ms: ' urn:microsoft-com:wmc-1-0' is not a valid URI
ot xmlns="urn:schemas-upnp-org:device-1-0" xmlns:ms=" urn:microsoft-com:wmc-1-0"
                                                                               ^
new device: Xbox 360 :: MediaRenderer
new UPnP device:
Xbox 360 (MediaRenderer)
error initializing audio decoder
Segmentation fault (core dumped)
john@john-feisty:~$ 

Also the within xbox360 i have no list for albums or artists just songs

---

### Post by Octagonal on 2007-11-08
hmm...
I'm assuming you'd only see this error if you're doing transcoding.
Correct me if I'm wrong but these aren't mp3 or wma files you're trying to play?
knowing what type of audio files you're playing may help determine the problem with the decoder...
If they're mp3 and wma files I would try turning on debug logging, by pressing "L" in the console if there could be more information given.

I would doubt the wireless router WRT54G would have any affect on it but I don't know for sure.

---

### Post by lime4x4 on 2007-11-08
I think the problem is i don't have flac support built in for some reason

iconv	true
uuid	false
taglib	false
imageMagick	false
libavformat (ffmpeg)	true
video transcoding (experimental)	true
lame	true
twolame	false
ogg/vorbis	true
musepack	false
flac	false
flac	false

How do i add flac support?

---

### Post by lime4x4 on 2007-11-08
Encoder
LAME	enabled
TwoLAME	compiled without TwoLame support
active encoder	LAME
Decoder
Vorbis	enabled
MusePack	compiled without MusePack support
FLAC	compiled without FLAC support

---

### Post by lime4x4 on 2007-11-08
by the way this is how i installed fuppes

$ svn co [http://fuppes-svn.ulrich-voelkel.de/trunk](http://fuppes-svn.ulrich-voelkel.de/trunk) fuppes
$ cd fuppes
$ autoreconf -vfi
$ ./configure --enable-video-transcoding
$ make
$ sudo make install
$ sudo ldconfig

---

### Post by jfank on 2007-11-08
I got a Xbox 360, and it is awesome.  I have another Xbox 360, but it's not setup to play games right now because I modded it to a Linux computer.  Still getting that set up and figure out how to use it. lol

---

### Post by lime4x4 on 2007-11-08
well i decided to recompile after installing all the stuff for flac now i get this error when tryinh to "make"

john@john-feisty:~/fuppes$ make
Making all in src
make[1]: Entering directory `/home/john/fuppes/src'
if test -e "../version.sh"; then \
                ../version.sh; \
        fi
make  all-am
make[2]: Entering directory `/home/john/fuppes/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib   -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg    -I/usr/include/libxml2      -D_FILE_OFFSET_BITS=64    -g -O2   -MT UPnPAction.lo -MD -MP -MF .deps/UPnPAction.Tpo -c -o UPnPAction.lo `test -f 'lib/UPnPActions/UPnPAction.cpp' || echo './'`lib/UPnPActions/UPnPAction.cpp
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/include/libxml2 -D_FILE_OFFSET_BITS=64 -g -O2 -MT UPnPAction.lo -MD -MP -MF .deps/UPnPAction.Tpo -c lib/UPnPActions/UPnPAction.cpp  -fPIC -DPIC -o .libs/UPnPAction.o
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/include/libxml2 -D_FILE_OFFSET_BITS=64 -g -O2 -MT UPnPAction.lo -MD -MP -MF .deps/UPnPAction.Tpo -c lib/UPnPActions/UPnPAction.cpp -o UPnPAction.o >/dev/null 2>&1
mv -f .deps/UPnPAction.Tpo .deps/UPnPAction.Plo
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib   -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg    -I/usr/include/libxml2      -D_FILE_OFFSET_BITS=64    -g -O2   -MT FileDetails.lo -MD -MP -MF .deps/FileDetails.Tpo -c -o FileDetails.lo `test -f 'lib/ContentDirectory/FileDetails.cpp' || echo './'`lib/ContentDirectory/FileDetails.cpp
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/include/libxml2 -D_FILE_OFFSET_BITS=64 -g -O2 -MT FileDetails.lo -MD -MP -MF .deps/FileDetails.Tpo -c lib/ContentDirectory/FileDetails.cpp  -fPIC -DPIC -o .libs/FileDetails.o
lib/ContentDirectory/FileDetails.cpp:40:29: error: wand/MagickWand.h: No such file or directory
/usr/include/ffmpeg/avcodec.h:2432: warning: attribute ignored in declaration of 'struct ImgReSampleContext'
/usr/include/ffmpeg/avcodec.h:2432: warning: attribute for 'struct ImgReSampleContext' must follow the 'struct' keyword
/usr/include/ffmpeg/avcodec.h:2437: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2444: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2448: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2450: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avformat.h:282: warning: 'AVFrac' is deprecated (declared at /usr/include/ffmpeg/avformat.h:118)
lib/ContentDirectory/FileDetails.cpp: In member function 'bool CFileDetails::GetImageDetails(std::string, SImageItem*)':
lib/ContentDirectory/FileDetails.cpp:249: error: 'MagickBooleanType' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:249: error: expected `;' before 'status'
lib/ContentDirectory/FileDetails.cpp:250: error: 'MagickWand' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:250: error: 'magick_wand' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:252: error: 'NewMagickWand' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:253: error: 'status' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:253: error: 'MagickReadImage' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:255: error: 'MagickFalse' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:257: error: 'ExceptionType' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:257: error: expected `;' before 'severity'
lib/ContentDirectory/FileDetails.cpp:259: error: 'severity' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:259: error: 'MagickGetException' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:260: error: 'GetMagickModule' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:261: error: 'MagickRelinquishMemory' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:263: error: 'DestroyMagickWand' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:267: error: 'MagickGetImageWidth' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:268: error: 'MagickGetImageHeight' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:270: error: 'DestroyMagickWand' was not declared in this scope
make[2]: *** [FileDetails.lo] Error 1
make[2]: Leaving directory `/home/john/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/john/fuppes/src'
make: *** [all-recursive] Error 1
john@john-feisty:~/fuppes$

---

### Post by Octagonal on 2007-11-09
According to the Fuppes wiki:

> 
This will build the latest versions of both ffmpeg and fuppes with all dependencies fulfilled (except ImageMagick since it is currently non-working in fuppes source). Fuppes transcoding will be enabled using these build steps.

(Tested against ffmpeg rev 10867 and fuppes rev 551) 


So you may want to configure as described on the wiki: [http://fuppes.ulrich-voelkel.de/wiki/index.php/Compiling_on_Linux](http://fuppes.ulrich-voelkel.de/wiki/index.php/Compiling_on_Linux)
> 
./configure --prefix=/usr --disable-imagemagick --enable-video-transcoding


hopefully that will resolve the error messages you're seeing during make.

---

### Post by xluryan on 2007-11-12
When I try to install fuppes I get the following:

```

ryan@freedom:~/Desktop$ svn co http://fuppes-svn.ulrich-voelkel.de/trunk fuppes
...
Checked out revision 552.
ryan@freedom:~/Desktop$ cd fuppes/
ryan@freedom:~/Desktop/fuppes$ autoreconf -vfi
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal --force 
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf --force
configure.in:11: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
ryan@freedom:~/Desktop/fuppes$ 

```

Any ideas?

---

### Post by lmellor on 2007-12-03
HI, I've followed just about every tutorial going on this forum (and on the fuppes site) yet I still can't get my 360 to play ball, fuppes can clearly see the 360 is switched on yet the 360 cannot see fuppes, any suggestions, I am asking mainly because you have yours working and so I guess you have overcome this hurdle at soem point or another.

I am not running any firewall as far as I know, I am on ubuntu 7.10 gutsy amd64, any suggestions?

TIA.

Luke.

---

### Post by ukripper on 2007-12-03
I have xbox360 but i just use it for gaming(as i prefer it that way)! Divx player are so cheap nowadays no point making your xbox360 work harder, giving extra overhead to processor.

All in one divx player plays everything for me (cost me only 30 £) pictures, movies, videos, music ( ofcourse doesn't play games though, that is why I have xbox360  at first place):)

---

### Post by lmellor on 2007-12-03
This doesn't help much, I've got a modded xbox for those purposes, my main need is some way of streaming my 40gb+ of music to my xbox 360 to get rid of the annoying dance music that is scattered all over the games that I buy.  Great games, terrible music.

Also with the addition of divx to the 360 this month I figured that my aging xbox will finally be laid to rest (except for emulation purposes of course).

Anybody else got anyideas as to how I can get this thing to work properly? I have been considering booting into windows and comiling fuppes for that to see if it plays ball.

---

### Post by ukripper on 2007-12-03
I was running loads of stuff on  self modded xbox till last year. At that time it was the best alternative to any other products in market but as the competition got better,  products are readily available to suit your needs and much cheaper. I have changed my policy to just use what it is built for!

 Except for computer customisation which I enjoy doing.

---

### Post by lmellor on 2007-12-03
> **ukripper said:**
> just use what it is built for!

Am I not correct in thinking that it was built as a multimedia home unit? Therefore I am trying to use it for what it was built for, just without windows getting in the way.

I don't mean to be rude but if you're not going to help me then please leave me alone, I don't want to buy a £30 divx player, that won't accept xvid content down a wire, nor will it put music on my 360.

Stop wasting my time and go annoy someone else with pointless talk.

:guitar:

---

### Post by ukripper on 2007-12-04
> **lmellor said:**
> Am I not correct in thinking that it was built as a multimedia home unit? Therefore I am trying to use it for what it was built for, just without windows getting in the way.

I don't mean to be rude but if you're not going to help me then please leave me alone, I don't want to buy a £30 divx player, that won't accept xvid content down a wire, nor will it put music on my 360.

Stop wasting my time and go annoy someone else with pointless talk.

:guitar:

Well mate I am not annoying you as this forum doesn't belong to you ( this is ubuntu community forum) and i am helping other people not you. Just providing them with alternate information. Stop being a moaning cow! And let other lot decide what option they like.

You can take it or leave it. No one is forcing you to take everything written here. Someone else might see point who is not as thick.

---

### Post by Joeb454 on 2007-12-04
Ok lets just stop arguing and remember that the Xbox 360 December Update is today, and from what I've read, it includes support for Divx/Xvid, I won't know for sure until I get home later on tonight, so I'll try and post back when I know for sure.

---

### Post by ukripper on 2007-12-04
> **Joeb454 said:**
> Ok lets just stop arguing and remember that the Xbox 360 December Update is today, and from what I've read, it includes support for Divx/Xvid, I won't know for sure until I get home later on tonight, so I'll try and post back when I know for sure.

Sounds good. have you got HD tv or LCD?

---

### Post by blueorder on 2007-12-04
I am also interested in this now that Xbox 360 has Xvid/Divx support. Would like to share videos on my Ubuntu server with the 360.

---

### Post by lmellor on 2007-12-04
> **ukripper said:**
> Well mate I am not annoying you as this forum doesn't belong to you ( this is ubuntu community forum) and i am helping other people not you. Just providing them with alternate information. Stop being a moaning cow! And let other lot decide what option they like.

You can take it or leave it. No one is forcing you to take everything written here. Someone else might see point who is not as thick.

Thick? I was asking about getting the 360 up and running, not where I can purchase hardware, you should check what questions have been asked before you go offering 'advice'.

Anyway it works now, somebody actually helped me.

Roll on the update, xvid support will be awesome!

BTW, you were annoying me in particular as you were answering MY question.

For anybody who is at the same point as I was then the answer lies in this thread...

[http://ubuntuforums.org/showthread.php?t=618781]("http://ubuntuforums.org/showthread.php?t=618781")

Thankfully some people offer solutions to problems.

---

### Post by ukripper on 2007-12-05
> **lmellor said:**
> Thick? I was asking about getting the 360 up and running, not where I can purchase hardware, you should check what questions have been asked before you go offering 'advice'.

Anyway it works now, somebody actually helped me.

Roll on the update, xvid support will be awesome!

BTW, you were annoying me in particular as you were answering MY question.

For anybody who is at the same point as I was then the answer lies in this thread...

[http://ubuntuforums.org/showthread.php?t=618781]("http://ubuntuforums.org/showthread.php?t=618781")

Thankfully some people offer solutions to problems.

Well see, you thought i was answering your question which is just your illusionary view and also you are not OP of this thread which proves i wasn't annoying you .

Nevermind  i am glad for you that someone really managed to help you.:)

---

### Post by Tadhg on 2007-12-05
finally got fuppes working with my Xbox, but still with a few problems. 

Firstly, it still seems like fuppes is transcoding divx/xvid, but surely i should be able to stream these videos normally with the new update?

Second, fuppes doesn't seem to be able to transcode ac3, as i get an error if i try to play any ac3 files.

EDIT: [http://ubuntuforums.org/showthread.php?t=618781]("http://ubuntuforums.org/showthread.php?t=618781") this fixed me up also.

---

### Post by Ash1984 on 2008-06-09
I have tried getting my divx files to stream to my xbox360, but I find it immensely easier to just copy the video file to a USB memory stick and plug it into the xbox360. Works just the same.

---

### Post by rugbert on 2008-07-18
Does Samba work with the 360? it works flawlessly with my XMBC, I JUST bought a 360 (like 2 hours ago) and if it will work with samba Im going to retire my XB1

---

### Post by mushroomblue on 2008-11-13
> **rugbert said:**
> Does Samba work with the 360? it works flawlessly with my XMBC, I JUST bought a 360 (like 2 hours ago) and if it will work with samba Im going to retire my XB1

you'll want to keep your original Xbox if it's running XBMC. it does smb, upnp, and supports every format ever uploaded on the internet. it's only drawback is HD support; 733Mhz isn't exactly beefy enough for most HD content.

the 360 can do up to 1080i (for mp4/xvid or h.263 - 1080p doesn't run well at all), but you're limited to very few formats. and it only uses an intentionally-broken UPnP spec to communicate. if you install TVersity (in windows) or acquire and install twonkyvision (in linux), you'll have the most painless solution. if you don't mind pain and headaches, fuppes works well, and transcodes, and is free.

if I had XBMC on a faster machine than an xbox, I'd never use anything else. best media client software, hands down.

---

