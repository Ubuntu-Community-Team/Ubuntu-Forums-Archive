---
title: "Compile ffmpeg with Vhook in 9.04"
date: 2009-05-09
forum: General Help
---

### Post by DeeMenace on 2009-05-09
Does anyone know how I can install or compile ffmpeg with vhook support in 9.04 ? when I run ffmpeg from terminal it says --disabled-vhook so I guess it's there but just not enabled? I tried to download the source using apt-get source ffmpeg, but it gave me an error when I ran make complaining about libavcodec and some mpeg4 codecs. It doesn't seem to matter how i configure it before I run make either. Anyone have any ideas ?

---

### Post by DeeMenace on 2009-05-09
anyone ? bump*

---

### Post by mc4man on 2009-05-09
A couple of things
First from a ffmpeg build on jaunty live cd
> In file included from vhook/drawtext.c:48:
./libavformat/framehook.h:25:2: warning: #**warning VHOOK is deprecated.** Please help finishing libavfilter instead of wasting your time writing new filters for this crappy filter system.


That being said you can build ffmpeg with it enabled, **whether it works right or at all I don't know.**

In the jaunty ver. you have it's not just a matter of "--disabled-vhook", but also this ( from confflags
> confflags += --enable-avfilter
confflags += --enable-avfilter-lavf

Any way it seems you need some help with the build-deps and building
I'd suggest you use this thread as a guide

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Follow everything exactly except **you can't use the current svn** (vhook has been removed

So substitute an earlier revision and then pick back up on his configure line (no need to specify --enable-vhook

You could start with the 0.5 source and *if need be work back from there*
(at very bottom of page, dl, extract, cd to the extracted folder and pick up at the configure line from the how to:
[http://www.ffmpeg.org/download.html](http://www.ffmpeg.org/download.html)

Ex.

> ubuntu@ubuntu:~/ffmpeg-0.5$ ./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-post-proc
install prefix            /usr/local
source path               /home/ubuntu/ffmpeg-0.5
,,,,,,clipped
static                    yes
shared                    no
postprocessing support    yes
software scaler enabled   no
new filter support        no
filters using lavformat   no
video hooking             yes
Imlib2 support            yes
.....clipped


May or may not be applicable (from here [http://graphcomp.com/ffmpeg/](http://graphcomp.com/ffmpeg/)

 >      NOTE: support for GIF is enabled by default in normal FFMPEG builds... however to support PNGs, you will need to do a custom build of FFMPEG with PNG as a registered image type.

      To enable PNG support, you need to do the following:
          o uncomment AVImageFormat for png in libavformat/allformats.h
          o uncomment av_register_image_fromat for png in libavformat/allformats.c
          o rebuild FFMPEG 



( again don't now if this is of any value ...?

---

### Post by DeeMenace on 2009-05-10
mc4man I can't thank you enough :) I don't know how many times I went to this page: [http://www.ffmpeg.org/download.html](http://www.ffmpeg.org/download.html) and didn't see the link to download at the bottom haha! once I got that I followed the directions in the other post except the svn stuff and it worked great. Thank you Thank you Thank you :)

---

