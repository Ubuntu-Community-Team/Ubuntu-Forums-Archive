---
title: "how to install Transcode from source, with last ffmpeg and libmpeg2"
date: 2005-07-15
forum: Desktop Environments
---

### Post by skyboy on 2005-07-15
Hi, this is my first HOWTO, so well, you know :)

Ok, I tried to install transcode this afternoon and couldn't get any rep (even debian-marillat) to work fine with unmet dependencies. So, I decided to take to bull by the horns and to compile everything from source. And trust me, it wasn't as simple as it sounds. (and I'm used to use source and compile)

so, lets start by downloading the sources you will need :

1 - from [http://www.transcoding.org](http://www.transcoding.org) 
download  latest version : [http://kraymer.de/mirroring/transcode-1.0.0.tar.gz](http://kraymer.de/mirroring/transcode-1.0.0.tar.gz)
 
2- from [http://ffmpeg.sourceforge.net](http://ffmpeg.sourceforge.net)
download latest version : [http://sourceforge.net/project/showfiles.php?group_id=16082](http://sourceforge.net/project/showfiles.php?group_id=16082)  (when I write this version 0.4.9-pre1)

3- from [http://libmpeg2.sourceforge.net/](http://libmpeg2.sourceforge.net/)
download also latest version (mpeg2dec-0.4.0b) : [http://libmpeg2.sourceforge.net/files/mpeg2dec-0.4.0b.tar.gz](http://libmpeg2.sourceforge.net/files/mpeg2dec-0.4.0b.tar.gz)

4- uncompress all the files and lets start !

5- start with libmpge2
a simple ./configure && make && sudo make install    
should be enough

6 - Now compile ffmpeg, but be carefull. Indeed, in order to get transcode to work, you have to enable the shared library so libavcodec can be installed and used by other application

so to configure :
./configure --enable-shared
(I also --enable-mp3lame --enable-vorbis) 

then make && sudo make install

check you have libavcodec installed with :
$ dpkg -l | grep libavcodec
you should have :
ii  libavcodec-dev 0.cvs20050121- development files for libavcodec
rc  libavcodec2    0.4.9-pre1-0.4 Library to encode decode multimedia streams

after that you need to do something, otherwise transcode will not compile, eventhough you have everything installed :

check where your libavcodec-O.4.9-pre1.so is installed
$whereis libavcodec-0.4.9-pre1so

then make a link :
$ sudo ln -s /usr/local/lib/libavcodec-0.4.9-pre1.so /usr/lib/libavcodec.so

this is to avoid having the error "undefined reference to `dts_frame'"

then you can compile transcode :
go to transcode directory :
$./configure && make && sudo make install

if you want to enable or disable more, look here : [http://www.transcoding.org/cgi-bin/transcode?Building_Transcode](http://www.transcoding.org/cgi-bin/transcode?Building_Transcode)

if you have trouble with "$sudo make install" telling you you have already /usr/local/man installed, remove it (at least that was this only possibility for me)
and $sudo make install 

now you should be done
NOTE : you might need to install some extra library, check your configure output. (this depend on your install)

--
###################
[http://thisisallaround.freezee.org](http://thisisallaround.freezee.org)
###################

---

