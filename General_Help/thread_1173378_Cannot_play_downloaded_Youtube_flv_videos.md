---
title: "Cannot play downloaded Youtube flv videos"
date: 2009-05-29
forum: General Help
---

### Post by xwhisper on 2009-05-29
I cannot make any youtube videos to be played after downloading. Mplayer spits Unsupported video codec zillion times and shows:
```
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
IMediaObject ERROR: 0x88dfa1b  input format not accepted (0x80040205 : -2147220987)
ERROR: Could not open required DirectShow codec wmspdmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dshow] Win32/DirectShow decoders
Win32 LoadLibrary failed to load: wmavds32.ax, /usr/lib/win32/wmavds32.ax, /usr/local/lib/win32/wmavds32.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=wmavds32.ax, r=0xa75bbfa)
ERROR: Could not open required DirectShow codec wmavds32.ax.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0xA.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video

```
Strange, only Totem manages to play them somehow, but there is no audio synch at all. VLC and Smplayer also fail. Avidemux can't open the file. I have full set of codecs: w32codecs, non-free-codecs, x264 and the ones from Mplayers' site. Any ideas?

---

### Post by paradigm2 on 2009-05-29
Did you install ubuntu-restricted-extras ?

---

### Post by andrew.46 on 2009-05-29
Hi xwhisper,

It is unusual that youtube videos would require the sort of codecs being asked for by MPlayer. In fact youtube videos are more usually flv + mp3 or h264 + aac and these formats do not require the extra codecs.

Can you post a link to one of these youtube videos and also mention how you are downloading them?

All the best,

Andrew

---

### Post by mc4man on 2009-05-29
> ..................??
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
.............. ect

I think you cut off the beginning where mplayer was looking for something else that it couldn't find, so then it starts working down through the all the possibilities, ending with wmavds32.ax. (none of which where found.

Noting that it's looking in "/usr/lib/win32", "/usr/local/lib/win32"

Most times (particularly for w32codecs) they're in /usr/lib/codecs and there is a folder  in /usr/lib named 'win32' that has links that point to /usr/lib/codecs (or similar setup in /usr/local

Check the for the actual location of your codecs and if there is a win32 folder the links aren't broken

---

### Post by xwhisper on 2009-05-30
For example: [http://www.youtube.com/watch?v=ahk4zVB2-c0](http://www.youtube.com/watch?v=ahk4zVB2-c0)
I just grab the video from /tmp folder (or using DownloadHelper sometimes)
Link in /usr/lib/ is fine.
Also strange is the fact that ONLY youtube videos won't play (all other sites are working fine). Totem is the only player that plays youtubies (with some problems)

Offtopic: where I can find a flv video that is not in /tmp. DownloadHelper also cannot detect it:
[http://www.suosikki.tv/musa/phoenix-effect-king-see-no-evil](http://www.suosikki.tv/musa/phoenix-effect-king-see-no-evil)

---

### Post by andrew.46 on 2009-05-30
Hi xwhisper,

> **xwhisper said:**
> For example: [http://www.youtube.com/watch?v=ahk4zVB2-c0](http://www.youtube.com/watch?v=ahk4zVB2-c0)
I just grab the video from /tmp folder (or using DownloadHelper sometimes)
Link in /usr/lib/ is fine.

I downloaded this video, although I will admit to being a youtube-dl fan so this is what I used, and it played flawlessly as follows:

```

andrew@skamandros~/Desktop$ mplayer ahk4zVB2-c0.flv 
MPlayer SVN-r29328-4.2.4 (C) 2000-2009 MPlayer Team

Playing ahk4zVB2-c0.flv.
libavformat file format detected.
[flv @ 0x8f3e3c0]skipping flv packet: type 18, size 294, flags 0
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x180  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
**[COLOR="Purple"]Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
**[COLOR="Purple"]Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)[/COLOR]**
==========================================================================
AO: [oss] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 180 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x180 => 320x180 Planar YV12 
A: 201.8 V: 201.8 A-V:  0.021 ct:  0.018   0/  0  1%  0%  0.4% 0 0 

Exiting... (End of file)

```

Can you post your full terminal output with the same file? As you can see it is a bog standard low quality flv with low bitrate mp3 sound. MPlayer *should* have no trouble with it. Who on earth is the big man in the white suite eating a rose btw?

> Offtopic: where I can find a flv video that is not in /tmp. DownloadHelper also cannot detect it:
[http://www.suosikki.tv/musa/phoenix-effect-king-see-no-evil](http://www.suosikki.tv/musa/phoenix-effect-king-see-no-evil)

I am not familiar with DownloadHelper but if the file is labelled .flv you can search your system for *all* flvs:

```
sudo find / -iname '*.flv'
```

All the best,

Andrew

---

### Post by xwhisper on 2009-05-30
```
[flv @ 0x8837aa8]Unsupported video codec (7)
[flv @ 0x8837aa8]skipping flv packet: type 97, size 7627016, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 70, size 320510, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 89, size 14578864, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 213, size 12123592, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 88, size 9790671, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 58, size 9532705, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 130, size 12232894, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 149, size 15503486, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 102, size 6255240, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 219, size 12082630, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 32, size 294460, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 248, size 16121710, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 21, size 13436232, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 172, size 8350159, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 35, size 11444606, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 177, size 4393517, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 3, size 843008, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 0, size 3611, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 97, size 16670870, flags 0
[flv @ 0x8837aa8]skipping flv packet: type 235, size 1731212, flags 0
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  []  0x0  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Cannot find codec matching selected -vo and video format 0x7.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
IMediaObject ERROR: 0x88dfa1b  input format not accepted (0x80040205 : -2147220987)
ERROR: Could not open required DirectShow codec wmspdmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dshow] Win32/DirectShow decoders
Win32 LoadLibrary failed to load: wmavds32.ax, /usr/lib/win32/wmavds32.ax, /usr/local/lib/win32/wmavds32.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=wmavds32.ax, r=0x944dc0a)
ERROR: Could not open required DirectShow codec wmavds32.ax.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0xA.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)

```
That's it. The first line is repeated zillion times and gnome-terminal just won't show me the first lines after starting. Maybe it will fix itself after I upgrade to Jaunty. It was working fine before. I never messed root dir, just my own /home.
The band: [http://en.wikipedia.org/wiki/Pero_Defformero](http://en.wikipedia.org/wiki/Pero_Defformero)
In two  words: Serbian rock band combining Balkan music with progressive rock.

---

### Post by andrew.46 on 2009-05-30
Hi xwhisper,

> **xwhisper said:**
> The first line is repeated zillion times and gnome-terminal just won't show me the first lines after starting. Maybe it will fix itself after I upgrade to Jaunty. It was working fine before. I never messed root dir, just my own /home.

It could very well be that your copy of MPlayer is a little damaged, although it is difficult to tell. A safe thing to do would be to use the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") MPlayer and install the w32codec pack from there as well. This will get you a more capable version of MPlayer and will also place the codecs correctly for you.

Before doing that perhaps you could test the flv that I downloaded and played, just to see if there is a problem with your collection method rather than MPlayer. I have temporarily placed this file on my website and it can be downloaded as:
```

wget http://www.andrews-corner.org/samples/Pero_Defformero.flv
```

If that does not play I would recommend the Medibuntu MPlayer.

> The band: [http://en.wikipedia.org/wiki/Pero_Defformero](http://en.wikipedia.org/wiki/Pero_Defformero)
In two  words: Serbian rock band combining Balkan music with progressive rock.

That explains the resemblance to the eurovision song contest that I see every now and then :-).

Andrew

---

### Post by xwhisper on 2009-05-31
Mplayers and codecs are from there, but you found the answer: the video is playing well from your site. What should I do now? Which way did you used to get it? And why only on youtube...

---

### Post by andrew.46 on 2009-05-31
Hi xwhisper,

> **xwhisper said:**
> Mplayers and codecs are from there, but you found the answer: the video is playing well from your site. What should I do now? Which way did you used to get it? And why only on youtube...

Interesting. I have come across this problem before where people have downloaded youtube videos using either /tmp or some sort of downloader and the flvs have been a little awry. I have never actually tracked down the actual problem but it certainly exists, perhaps youtube changes things a little every now and then?

It is an easy way to start a holy war but I can give you my own preferred method of downloading youtube videos:

youtube-dl: Download videos from YouTube.com
[http://bitbucket.org/rg3/youtube-dl/wiki/Home](http://bitbucket.org/rg3/youtube-dl/wiki/Home)

This is a small commandline utility, actually a python script, that is kept up to do date with a release usually every 4 weeks and it is a good idea to keep it up to date. Installation of the current version is:

```

$ sudo apt-get remove youtube-dl
$ wget http://bitbucket.org/rg3/youtube-dl/raw/2009.05.30/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl

```

You will note that when you update the address of the script will change each month, I have been trying to script regular updates with complete failure so far :-). Check your version as follows:

```

andrew@skamandros~$ youtube-dl --version
2009.05.30

```

Full usage can be seen with 'youtube-dl --help' but the simple syntax for your particular file is as follows:

```
$ cd Desktop
$ youtube-dl 'http://www.youtube.com/watch?v=ahk4zVB2-c0'
```

If you were interested in delving a little deeper into youtube-dl the following might whet your appetite a little:

```
youtube-dl -b 'http://www.youtube.com/watch?v=ahk4zVB2-c0'
```

and this downloads a 54 meg high quality mp4 of the same clip from youtube. h264 video and aac sound. How cool is that :-).

All the best,

Andrew

---

### Post by xwhisper on 2009-06-12
That worked, but after upgrading to Jaunty the problem fixed itself. I have no reason why. Even previously downloaded "broken" videos work fine now. Only Avidemux can't open them.

---

### Post by mikeh on 2009-07-15
I'm getting the same problem with the high-quality youtube FLV downloads in Jaunty with medibuntu.
  Can play the low-ref .flv and .mp4 versions, but not the HQ .flv in mplayer. So I guess it needs a new codec. VLC can play the files OK.


```

[flv @ 0x883f748]Unsupported video codec (7)
.
.
[flv @ 0x883f748]skipping flv packet: type 165, size 2062799, flags 0
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  []  0x0  0bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Opening video filter: [pp=lb]
==========================================================================
Cannot find codec matching selected -vo and video format 0x7.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
IMediaObject ERROR: 0x88e761b  input format not accepted (0x80040205 : -2147220987)
ERROR: Could not open required DirectShow codec wmspdmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dshow] Win32/DirectShow decoders
Win32 LoadLibrary failed to load: wmavds32.ax, /usr/lib/win32/wmavds32.ax, /usr/local/lib/win32/wmavds32.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=wmavds32.ax, r=0x8f1559a)
ERROR: Could not open required DirectShow codec wmavds32.ax.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0xA.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video

```

---

### Post by meka4996 on 2009-08-09
Go to [http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)
or Google it: flv flash Totem internal data stream vlc undf

---

