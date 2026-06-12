---
title: "ffmpeg segfault"
date: 2009-05-10
forum: General Help
---

### Post by djbushido on 2009-05-10
I'm getting an ffmpeg segfault using libx264 (libavcodec-unstripped installed) trying to convert a 722Mb movie file (Star Wars VI in case anyone wanted to know). I made sure file permissions were ugo=rwx to see if that helped, but didn't. I have also tried to do this as sudo, but to no avail. It was actually sudo su. I lied.
Anyway, if anybody could help that would be great.

---

### Post by andrew.46 on 2009-05-11
Hi djbushido,

> **djbushido said:**
> I'm getting an ffmpeg segfault using libx264 (libavcodec-unstripped installed) trying to convert a 722Mb movie file

Perhaps you could try the Fakeoutdoormsan's guide to utilising the latest FFmpeg from svn:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

If you *still* get a segfault with the most recent version you might be best to post the full commandline + terminal output here and see if a solution can be found.

All the best,

Andrew

---

### Post by djbushido on 2009-05-11
The problem is that so much of my system depends on libx264 that I can't remove it without serious problems, then reinstalling would overwrite it.
I need to use just the ubuntu ffmpeg, that is why I installed the unstripped avcodec. I will post the full command later.

---

### Post by andrew.46 on 2009-05-12
Hi djbushido,

> **djbushido said:**
> The problem is that so much of my system depends on libx264 that I can't remove it without serious problems, then reinstalling would overwrite it.
I need to use just the ubuntu ffmpeg, that is why I installed the unstripped avcodec. I will post the full command later.

I am not completely sure about this but will the svn FFmpeg compile against the Jaunty libx264-dev? The Jaunty version is build 65 and the current svn configure script *should* work with this:

```

enabled libx264    && require  libx264 x264.h x264_encoder_open -lx264 -lm &&
                      { check_cpp_condition x264.h "**[COLOR="Red"]X264_BUILD >= 65"[/COLOR]** ||
                        die "ERROR: libx264 version must be >= 0.65."; }

```

although this would not be ideal as in general you should compile the newest x264 *and* the newest FFmpeg together.

Andrew

---

### Post by djbushido on 2009-05-12
I'm actually going to wait a little bit - I think the video was actually messed up (but not enough to destroy the entire thing - it's happened before) and I need to check and make sure that that's not the problem before messing with this.
And svn ffmpeg should compile against libx264 for jaunty. I actually don't need to compile against against the dev package, that would mean that I would have to rebuild it. As far as I know, FFmpeg just links to the libx264. I have no idea how avcodec-unstripped works though.
Anyway, will post back soon(ish) and see if it wasn't just the video.

---

### Post by djbushido on 2009-05-18
Nope, video was fine, grabbed the libx264 source and built a new ffmpeg against it, still getting segfaults. Help appreciated!
If someone could give me an mencoder script for this that would be wonderful. The current ffmpeg script i am using is: ```
ffmpeg -i $1 -acodec libfaac -ab 128k -s 320x240 -vcodec libx264 -b 500k -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -flags2 +mixed_refs -me_method umh -subq 6 -trellis 1 -refs 5 -coder 0 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 500k -maxrate 768k -bufsize 2M -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 13 -threads 0 -f mp4 $2
```
Long, but it's worked until now.

---

### Post by djbushido on 2009-05-18
Sorry for all the posting, but found an mencoder profile, but that is giving me a segfault too. Could it possibly be that libx264 or libfaac are messed up? They were working previously on jaunty, but I don't know what happened. This is really weird and I'd appreciate greatly any help in trying to get this fixed. Videos are a must for me. Anyway, thanks.

---

### Post by FakeOutdoorsman on 2009-05-18
Try using the libx264 presets instead of that bird's nest:
```
ffmpeg -i $1 -acodec libfaac -ab 128k -s 320x240 -vcodec libx264 -vpre hq -vpre baseline -b 500k -bt 500k -threads 0 $2
```
Of course there may be issues if you use latest FFmpeg with older x264.

---

### Post by andrew.46 on 2009-05-19
Hi djbushido,

> **djbushido said:**
> Sorry for all the posting, but found an mencoder profile, but that is giving me a segfault too.

Could you post the mencoder command / profile and the resulting terminal output?

Thanks,

Andrew

---

### Post by djbushido on 2009-05-19
Ok, using the FakeOutdoorsman script, here is the output:
```
brad@BradXFCE:~/Videos/Originals$ /home/brad/Videos/To\ be\ converted/walkman-simple.sh Star_Wars_VI.avi Star_Wars_VI.mp4 
FFmpeg version SVN-r18868, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on May 18 2009 16:08:46, gcc: 4.3.3
Input #0, avi, from 'Star_Wars_VI.avi':
  Duration: 02:14:48.16, start: 0.000000, bitrate: 751 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 716x364 [PAR 212:179 DAR 212:91], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 160 kb/s
File 'Star_Wars_VI.mp4' already exists. Overwrite ? [y/N] y
[libx264 @ 0x9dbcbb0]using SAR=159/91
[libx264 @ 0x9dbcbb0]using cpu capabilities: MMX2
[libx264 @ 0x9dbcbb0]profile Baseline, level 2.0
Output #0, mp4, to 'Star_Wars_VI.mp4':
    Stream #0.0: Video: libx264, yuv420p, 320x240 [PAR 159:91 DAR 212:91], q=10-51, 500 kb/s, 24k tbn, 23.98 tbc
    Stream #0.1: Audio: libfaac, 48000 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
/home/brad/Videos/To be converted/walkman-simple.sh: line 1:  8208 Segmentation fault      ffmpeg -i $1 -acodec libfaac -ab 128k -s 320x240 -vcodec libx264 -vpre hq -vpre baseline -b 500k -bt 500k -threads 0 $2

```
Noting that ffmpeg was built using svn and libx264-dev in the repos. Problems?

Also, here is the mencoder profile:```
[Walkman]
ScreenRatio=4:3
Manufacturer=Sony
Res1=320x240
ResAna1=320x180
ResExpand1=320x240
ARate=48000
ABRate=64
Format=lavf
lavfopts=format=mp4
FileType=mp4
Quality=30
lavcopts=aglobal=1:vglobal=1:vcodec=mpeg4:acodec=libfaac
MVolume=20
useMencoder=1
SubTitle=1
NTSCFrameRate1=14
NTSCFrameRateDeinterlace1=14
PALFrameRate1=14
MaxVBitrate=768
```
and the mencoder command:```
mencoder $1 -quiet -profile Walkman -o $2

``` and output:```
brad@BradXFCE:~/Videos/Originals$ /home/brad/Videos/To\ be\ converted/walkman-mencoder.sh Star_Wars_VI.avi Star_Wars_VI.mp4
MEncoder 2:1.0~rc2-0ubuntu19 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x2d4c90a4
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  716x364  24bpp  23.976 fps  578.8 kbps (70.7 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:716x364  fps:23.98  ftime:=0.0417
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [hqdn3d]
Opening video filter: [crop w=320 h=240]
Crop: 320 x 240, -1 ; -1
Opening video filter: [scale w=320 h=240]
Opening video filter: [pp=fd]
Opening video filter: [softskip]
Opening video filter: [pullup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
VDec: vo config request - 716 x 364 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar I420 as output csp (no 1)
Movie-Aspect is 2.33:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 10 -> 12
SwScaler: reducing / aligning filtersize 10 -> 12
SwScaler: reducing / aligning filtersize 8 -> 6
SwScaler: reducing / aligning filtersize 8 -> 6
[swscaler @ 0x883d3d0]SwScaler: BICUBIC scaler, from yuv420p to yuv420p using MMX2
[swscaler @ 0x883d3d0]SwScaler: using n-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x883d3d0]SwScaler: using n-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x883d3d0]SwScaler: using n-tap MMX scaler for vertical scaling (YV12 like)
[swscaler @ 0x883d3d0]SwScaler: 716x364 -> 320x240
x264 [info]: using SAR=559/320
x264 [info]: using cpu capabilities: MMX2
x264 [info]: profile Baseline, level 1.3
VIDEO CODEC ID: 28
AUDIO CODEC ID: 15002, TAG: 0
Writing header...
/home/brad/Videos/To be converted/walkman-mencoder.sh: line 1:  7204 Illegal instruction     mencoder $1 -quiet -profile Walkman -o $2

```
Mencoder is straight from the repos. So is libx264. Can I compile my own libx264 and insert that into where the repo is? Will try this (with checkinstall to allow for removal) and post if it helps.

---

### Post by andrew.46 on 2009-05-19
Hi djbushido,

I will leave FakeOutdoorsman to comment on the FFmpeg syntax as he is by far the more experienced with FFmpeg in general :-). In general though I believe that FFmpeg will do a *better* job than MEncoder with such conversions and the required syntax is almost always a lot clearer.

But for MEncoder:

> **djbushido said:**
> 
Also, here is the mencoder profile:
```
[Walkman]
ScreenRatio=4:3
Manufacturer=Sony
Res1=320x240
ResAna1=320x180
ResExpand1=320x240
ARate=48000
ABRate=64
Format=lavf
lavfopts=format=mp4
FileType=mp4
Quality=30
lavcopts=aglobal=1:vglobal=1:vcodec=mpeg4:acodec=libfaac
MVolume=20
useMencoder=1
SubTitle=1
NTSCFrameRate1=14
NTSCFrameRateDeinterlace1=14
PALFrameRate1=14
MaxVBitrate=768
```
and the mencoder command:```
mencoder $1 -quiet -profile Walkman -o $2

``` 

Unfortunately this is *not* a proper MEncoder profile, if you mean a set of definitions placed in $HOME/.mplayer/config:

```

PROFILES
To ease working with different configurations profiles can  be  defined
in  the  configuration  files.   A profile starts with its name between
square brackets, e.g. '[my-profile]'.  All following  options  will  be
part of the profile.  A description (shown by -profile help) can be de-
fined with the profile-desc option.  To end the profile, start  another
one  or use the profile name 'default' to continue with normal options.

```

The profile that you have given generates multiple errors and I suspect that it has been coped and pasted from a *script* rather than a *profile*. This leads to the error:

```
7204 Illegal instruction     mencoder $1 -quiet -profile Walkman -o $2
```

which is not really a segmentation fault, I think it is simply telling you that your profile is faulty. If you remain keen to use MEncoder and profiles it *can* be done but you will need to strip out 75% of this profile and rebuild it.

All the best,

Andrew

PS This profile uses mpeg4 video rather than encoding with x264?

---

### Post by djbushido on 2009-05-19
Yeah, the profile is messed up. However, when trying to convert the video without the profile, I did get a segfault. Believe it or not.
The ffmpeg syntax I'm pretty sure is right.
Also, the mp4 instead of libx264 is libavcodec, which I'm pretty sure will rely on libx264 anyway.

---

### Post by andrew.46 on 2009-05-19
Hi djbushido,

> **djbushido said:**
> Yeah, the profile is messed up. However, when trying to convert the video without the profile, I did get a segfault. Believe it or not.
The ffmpeg syntax I'm pretty sure is right.
Also, the mp4 instead of libx264 is libavcodec, which I'm pretty sure will rely on libx264 anyway.

If you wish to use MEncoder to use libx264 the syntax is:

```
-ovc x264 -x264encopts blah:blah=3:blah etc etc
```

while to use mpeg4 video:

```
-ovc lavc -lavcopts vcodec=mpeg4:acodec=libfaac etc etc
```

while to force an mp4 *container* rather than the native avi container:

```
-of lavf -lavfopts format=mp4
```

But I would still recommend FFmpeg for this purpose.

Andrew

---

### Post by djbushido on 2009-05-20
How would one alter the above profile to use x264? As far as I know, that it all that needs to change (although I guess I'll find out :)). I'm not wanting to use ffmpeg, because as stated, it's not working. I'm going to try and recompile my own libx264 and insert it with checkinstall, to see if that works. NOTE: I'll still be following the FakeOutdoorsman guide.

EDIT: What needs to be changed on the profile?
EDITEDIT: Woops, already said that.

---

### Post by djbushido on 2009-05-24
Still getting segfaults. Any other ideas? Please???

---

### Post by FakeOutdoorsman on 2009-05-24
> **djbushido said:**
> Still getting segfaults. Any other ideas? Please???

It segfaults with the latest FFmpeg and x264?  Does it segfault immediately, or later in the conversion process?  You may want to discuss this in the [ffmpeg-user](http://ffmpeg.org/contact.html) mailing list, or perhaps even [submit a bug report](http://ffmpeg.org/bugreports.html).  There are also knowledgeable users in the #ffmpeg IRC channel.  Just make sure to use a very recent FFmpeg and use a [pastebin](http://ffmpeg.pastebin.com/) to show your command and the complete output from FFmpeg if you ask questions on #ffmpeg.  I would be willing to test this video myself, but I assume it is quite large.

---

### Post by djbushido on 2009-05-25
Yeah, the entire star wars VI video is 725 mb on my computer. I will look into the pastebin, but will try converting another video to make sure that it's not that one. Other programs on my computer are segfaulting too, so I don't know if it's a system issue.

---

### Post by FakeOutdoorsman on 2009-05-25
Trying other videos is a good idea.  If the Star Wars video is the only problem then try to get just a section of the bad video.  Hopefully it won't segfault during this process:
```
ffmpeg -t 10 -i Star_Wars_VI.avi -acodec copy -vcodec copy startest.avi
```
Does FFmpeg segfault if you try to encode from *startest.avi*?  If it does you can make this sample available and I will test for the segfault as well.

---

### Post by djbushido on 2009-05-25
I am posting a link to a very nice Monty Python video that I can now not watch on my mp3 player because it segfaults. Good luck!
[URL="http://keepvid.com/?url=http%3A//www.youtube.com/watch%3Fv%3DzekiZYSVdeQ%26fmt%3D18"]
http://keepvid.com/?url=http%3A//www.youtube.com/watch%3Fv%3DzekiZYSVdeQ%26fmt%3D18[/URL]

---

### Post by djbushido on 2009-05-25
sorry for double post, but I can encode the startest video. I think what it is is that the segfault is a matter of time - 10 seconds isn't enough to make it segfault. Now I have the FOX fanfare for my mp3 player!!! I'll see if I can't use mencoder to try and do it.

EDIT: I can now get Mencoder to segfault. Previously it was a profile error:```
brad@BradXFCE:~/Videos/Originals$ mencoder -quiet -profile Walkman Star_Wars_VI.avi -o Star_Wars_VI.mp4
MEncoder 2:1.0~rc2-0ubuntu19 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Option default needs a parameter at line 15

Exiting... (config file error)
brad@BradXFCE:~/Videos/Originals$ mencoder -quiet -profile Walkman Star_Wars_VI.avi -o Star_Wars_VI.mp4
MEncoder 2:1.0~rc2-0ubuntu19 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x2d4c90a4
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  716x364  24bpp  23.976 fps  578.8 kbps (70.7 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:716x364  fps:23.98  ftime:=0.0417
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [hqdn3d]
Opening video filter: [crop w=320 h=240]
Crop: 320 x 240, -1 ; -1
Opening video filter: [scale w=320 h=240]
Opening video filter: [pp=fd]
Opening video filter: [softskip]
Opening video filter: [pullup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
VDec: vo config request - 716 x 364 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar I420 as output csp (no 1)
Movie-Aspect is 2.33:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 10 -> 12
SwScaler: reducing / aligning filtersize 10 -> 12
SwScaler: reducing / aligning filtersize 8 -> 6
SwScaler: reducing / aligning filtersize 8 -> 6
[swscaler @ 0x883d3d0]SwScaler: BICUBIC scaler, from yuv420p to yuv420p using MMX2
[swscaler @ 0x883d3d0]SwScaler: using n-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x883d3d0]SwScaler: using n-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x883d3d0]SwScaler: using n-tap MMX scaler for vertical scaling (YV12 like)
[swscaler @ 0x883d3d0]SwScaler: 716x364 -> 320x240
x264 [info]: using SAR=559/320
x264 [info]: using cpu capabilities: MMX2
x264 [info]: profile Baseline, level 1.3
VIDEO CODEC ID: 28
AUDIO CODEC ID: 15002, TAG: 0
Writing header...
Segmentation fault
brad@BradXFCE:~/Videos/Originals$
```
Any help still appreciated.
EDITNOTE: Using ffmpeg and libx264 from the FakeOutdoorsman guide, mencoder from repos.

---

### Post by andrew.46 on 2009-05-26
Hi djbushido,

> **djbushido said:**
> I am posting a link to a very nice Monty Python video that I can now not watch on my mp3 player because it segfaults. Good luck!
[URL="http://keepvid.com/?url=http%3A//www.youtube.com/watch%3Fv%3DzekiZYSVdeQ%26fmt%3D18"]
http://keepvid.com/?url=http%3A//www.youtube.com/watch%3Fv%3DzekiZYSVdeQ%26fmt%3D18[/URL]

I saw 2 variations on this video on that page so I downloaded both. The low quality flv file was:

```

Input #0, flv, from 'save-video.flv':
Duration: 00:02:35.40, start: 0.000000, bitrate: 64 kb/s
Stream #0.0: Video: flv, yuv420p, 320x240, 29.97 tbr, 1k tbn, 1k tbc
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s

```

while the mp4 file was:

```

Duration: 00:02:35.87, start: 0.000000, bitrate: 541 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
Stream #0.1(und): Video: h264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 59.94 tbc

```

A nice spread of codecs :-). All played without error with the svn MPlayer and I attach screenshots of this in progress. Have you thought of installing the svn MPlayer? The easiest way might be to use [RVM's PPA]("https://launchpad.net/~rvm/+archive/mplayer") if you were interested.

All the best,

Andrew

---

### Post by djbushido on 2009-05-26
The problem with mplayer is that it can't convert the video. At least, as far as I know. What I meant was that  I can't convert the videos because it segfaults.

---

### Post by andrew.46 on 2009-05-26
Hi djbushido,

> **djbushido said:**
> The problem with mplayer is that it can't convert the video. At least, as far as I know. What I meant was that  I can't convert the videos because it segfaults.

Oops I forgot that in Debian / Ubuntu the MPlayer source is compiled into 2 packages. If you compile the svn by *default* you get MPlayer and MEncoder.

Andrew

---

### Post by FakeOutdoorsman on 2009-05-26
> **djbushido said:**
> I am posting a link to a very nice Monty Python video that I can now not watch on my mp3 player because it segfaults. Good luck!
[URL="http://keepvid.com/?url=http%3A//www.youtube.com/watch%3Fv%3DzekiZYSVdeQ%26fmt%3D18"]
http://keepvid.com/?url=http%3A//www.youtube.com/watch%3Fv%3DzekiZYSVdeQ%26fmt%3D18[/URL]

No segfault here.  I converted both the flv and mp4 inputs using FFmpeg version SVN-r18936 with the following command:
```
ffmpeg -i seg.flv -acodec libfaac -ab 128k -s 320x240 -vcodec libx264 -vpre hq -vpre baseline -b 500k -bt 500k -threads 0 output.mp4
```
I'm not sure what to recommend to you now.  Perhaps you can run the commands on [Reporting a Bug To The FFmpeg Project](http://ffmpeg.org/bugreports.html) to get more useful information to pinpoint the problem.  I've never done this so I don't know if the debugging output will even be apprehensible to a non-developer such as myself.

---

### Post by djbushido on 2009-05-26
I've done some C(++) hacking in my time (since I was 12 actually - long story) but am getting some help on IRC. Will post back if anything works. Using gdb.

---

### Post by djbushido on 2009-05-30
Turns out the fault was faac. Re-compiled the lib, re-linked, etc., and now ffmpeg is working. Thanks for the help!

---

### Post by FakeOutdoorsman on 2009-05-30
> **djbushido said:**
> Turns out the fault was faac. Re-compiled the lib, re-linked, etc., and now ffmpeg is working. Thanks for the help!

How did you figure out the problem?  I was stumped.

---

### Post by djbushido on 2009-05-30
Two reasons:
1. There were three files in use: libfaac, libx264, and ffmpeg. Ffmpeg and libx264 were repeatedly recompiled. Only libfaac remains.
2. The actual reason was that in compile time, a binary ffmpeg_g is created. This is the debug version. Running this in gdb and doing a backtrace showed the error at libfaac. 

So basically doing a backtrace from the segfault solved the problem. Now I want to see if I can get the ubuntu repo defaults to work, because the new libx264 (in /usr/local) is causing problems.

---

### Post by andrew.46 on 2009-05-30
Hi djbushido,

> **djbushido said:**
> Turns out the fault was faac. Re-compiled the lib, re-linked, etc., and now ffmpeg is working. Thanks for the help!

Congrats for working that one out, I did not see that coming :-)

Andrew

---

### Post by FakeOutdoorsman on 2009-05-31
> **djbushido said:**
> Now I want to see if I can get the ubuntu repo defaults to work, because the new libx264 (in /usr/local) is causing problems.

Glad you solved the segfault.  What kind of problems are you having with the compiled x264?

---

