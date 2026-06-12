---
title: "Attn UK users with iPlayer Desktop Experience - trying to run under U12.04"
date: 2013-01-08
forum: Desktop Environments
---

### Post by phil_elvey on 2013-01-08
Hi all,

I'm trying to get iPlayer Desktop to work on my Ubuntu 12.04 machine.

I have installed Air and the iPlayer Desktop program all OK, and it starts up no worries.

The problem I have is when I browse the iPlayer site with either Firefox or Chromium, and find something to download and click the "Download via iPlayer Desktop" link, it just takes me to the "Install iPlayer" page, instead of the iPlayer Desktop programme picking up the download.

Has anyone had this experience and know how to resolve?

I'm currently using a fresh install of Ubuntu 12.04, 32-bit (have also tried 64-bit), with nothing else installed, but all updates run.

Cheers

---

### Post by Cheesemill on 2013-01-09
I gave up on the iPlayer Desktop application years ago when Adobe dropped support for the Air platform on Linux. Instead I use the command line tool get_iplayer along with a couple of aliases to make it easier to use.

 I have these 2 aliases in my ~/.bashrc file:
```
alias ipl='get_iplayer --nocopyright'
alias gipl='get_iplayer --nocopyright --output=~/Videos --tvmode=flashhd,flashvhigh,flashhigh,flashstd,flashnormal --get'
```It's now a simple task to use the ipl command to search for programmes...
```
rob@arch:~$ ipl star
Matches:
421:    Little Stargazing - -, BBC Two, Learning,Primary,TV, default
653:    Stargazing Challenges - -, BBC Two, Learning,Primary,TV, default
654:    Stargazing LIVE: Series 3 - 2. Back to Earth 1, Highlights, Factual,Nature & Environment,Science & Nature,TV, default
655:    Stargazing LIVE: Series 3 - Episode 1, BBC Two, Factual,HD,Nature & Environment,Science & Nature,TV, default,

INFO: 4 Matching Programmes
rob@arch:~$

```And then to use the gipl command to download the required programme in the highest quality available and then place the transcoded mp4 file into my Videos folder...
```

rob@arch:~$ gipl 655
Matches:
655:    Stargazing LIVE: Series 3 - Episode 1, BBC Two, Factual,HD,Nature & Environment,Science & Nature,TV, default,

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashvhigh1,flashvhigh2,flashvhigh3,flashvhigh4,flashhigh1,flashhigh2,flashstd1,flashstd2 modes will be tried for version default
INFO: Trying flashvhigh1 mode to record tv: Stargazing LIVE: Series 3 - Episode 1
INFO: File name prefix = Stargazing_LIVE_Series_3_-_Episode_1_b01py6vh_default                 
RTMPDump v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Starting download at: 0.000 kB
INFO: Metadata:
656238.696 kB / 3574.10 sec
Download complete
ffmpeg version 1.0.1 Copyright (c) 2000-2012 the FFmpeg developers
  built on Dec  7 2012 18:16:36 with gcc 4.7.2 (GCC)
  configuration: --prefix=/usr --enable-libmp3lame --enable-libvorbis --enable-libxvid --enable-libx264 --enable-libvpx --enable-libtheora --enable-libgsm --enable-libspeex --enable-postproc --enable-shared --enable-x11grab --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libschroedinger --enable-libopenjpeg --enable-librtmp --enable-libpulse --enable-libv4l2 --enable-gpl --enable-version3 --enable-runtime-cpudetect --disable-debug --disable-static
  libavutil      51. 73.101 / 51. 73.101
  libavcodec     54. 59.100 / 54. 59.100
  libavformat    54. 29.104 / 54. 29.104
  libavdevice    54.  2.101 / 54.  2.101
  libavfilter     3. 17.100 /  3. 17.100
  libswscale      2.  1.101 /  2.  1.101
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, flv, from '/home/rob/Videos/Stargazing_LIVE_Series_3_-_Episode_1_b01py6vh_default.partial.mp4.flv':
  Metadata:
    moovPosition    : 32
    avcprofile      : 77
    avclevel        : 30
    aacaot          : 2
    videoframerate  : 25
    audiochannels   : 2
  Duration: 00:59:34.14, start: 0.000000, bitrate: 1504 kb/s
    Stream #0:0: Video: h264 (Main), yuv420p, 832x468 [SAR 117:117 DAR 16:9], 25 tbr, 1k tbn, 50 tbc
    Stream #0:1: Audio: aac, 48000 Hz, stereo, s16
Output #0, mp4, to '/home/rob/Videos/Stargazing_LIVE_Series_3_-_Episode_1_b01py6vh_default.partial.mp4':
  Metadata:
    moovPosition    : 32
    avcprofile      : 77
    avclevel        : 30
    aacaot          : 2
    videoframerate  : 25
    audiochannels   : 2
    encoder         : Lavf54.29.104
    Stream #0:0: Video: h264 ([33][0][0][0] / 0x0021), yuv420p, 832x468 [SAR 117:117 DAR 16:9], q=2-31, 1k tbn, 1k tbc
    Stream #0:1: Audio: aac ([64][0][0][0] / 0x0040), 48000 Hz, stereo
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame=89351 fps=34291 q=-1.0 Lsize=  655692kB time=00:59:34.14 bitrate=1502.9kbits/s    
video:611770kB audio:41332kB subtitle:0 global headers:0kB muxing overhead 0.396470%
INFO: Recorded /home/rob/Videos/Stargazing_LIVE_Series_3_-_Episode_1_b01py6vh_default.mp4

INFO: Downloaded Thumbnail to '/home/rob/Videos/Stargazing_LIVE_Series_3_-_Episode_1_b01py6vh_default.jpg'
rob@arch:~$ 
```If you are using 12.04 then the version of get_iplayer in the repositories is out of date, you will need to use a PPA to install the latest version:
```
sudo add-apt-repository ppa:jon-hedgerows/get-iplayer
sudo apt-get update
sudo apt-get install get-iplayer
```There is more you can do with get_iplayer once you get beyond the basics, like streaming live broadcasts directly into VLC, timeshifting radio broadcasts, and much more.

---

### Post by phil_elvey on 2013-01-09
Hi Cheesemill,

Thanks for the pointers on get_iplayer.  I have started playing with it, and it looks better than what I originally thought.

I would still like to see if the iPlayer Desktop can work if anyone has it going...?

In the meantime I will keep experimenting with get_iplayer

Cheers

---

### Post by phil_elvey on 2013-01-09
Hi Cheesemill,

I've done some more digging, and found the web PVR part of get_iplayer - now this makes it a real iPlayer Desktop alternative, except better! Yay!

Ok there's just one problem and I'm hoping you can help.

I don't want the programmes to download in HD, but in the next best format - I take it this is flashvhigh (instead of flashhd)?

In the web PVR I've set the default recording modes and excluded flashhd.
I then added a program to the PVR list (Miranda), and when checking the list it correctly shows the modes (correctly excluding flashhd).

But when I run the PVR (I'm running from the command line, but that shouldn't make any difference?) it downloads the Miranda episodes in flashhd!  Grrrr!

Do you have any clues on getting it to stop using flashhd, and the modes as specified?

Here's the pvr file under ~/.get_iplayer/pvr
```

fields name
modes flashvhigh,flashhigh,flashstd,flashnormal,flashaac,flashaacstd,flashaaclow,flashaudio,realaudio,wma
output /home/phil/TV/iPlayer
subtitles 0
thumb 0
type tv
versionlist default
search0 ^Miranda: Series 3$
```

Here's the output when I run the PVR command:
```
Running PVR Searches:
_Miranda_Series_3_name_tv
Matches:
461:	Miranda: Series 3 - 3. The Dinner Party, BBC One, Audio Described,Comedy,Highlights,Popular,Sitcoms,TV, default,audiodescribed,
462:	Miranda: Series 3 - 1. It Was Panning, BBC One, Audio Described,Comedy,Sitcoms,TV, default,audiodescribed

INFO: 2 Matching Programmes
INFO: Checking existence of default version
INFO: flashhd1,flashhd2,flashvhigh1,flashvhigh2,flashhigh1,flashhigh2 modes will be tried for version default
INFO: Trying flashhd1 mode to record tv: Miranda: Series 3 - 3. The Dinner Party
INFO: File name prefix = Miranda_Series_3_-_3._The_Dinner_Party_b01pvlys_default                 
RTMPDump v2.4-n37-git4e06e21-ppa6~natty
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: RTMP_Connect1, handshake failed.
INFO: Command exit code 3 (raw code = 768)
WARNING: Failed to stream file /home/phil/TV/iPlayer/Miranda_Series_3_-_3._The_Dinner_Party_b01pvlys_default.partial.mp4.flv via RTMP
INFO: skipping flashhd1 mode
INFO: Trying flashhd2 mode to record tv: Miranda: Series 3 - 3. The Dinner Party
INFO: File name prefix = Miranda_Series_3_-_3._The_Dinner_Party_b01pvlys_default                 
RTMPDump v2.4-n37-git4e06e21-ppa6~natty
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Starting download at: 0.000 kB
INFO: Metadata:
INFO:   duration              1711.15
INFO:   moovPosition          32.00
INFO:   width                 1280.00
INFO:   height                720.00
INFO:   videocodecid          avc1
INFO:   audiocodecid          mp4a
INFO:   avcprofile            100.00
INFO:   avclevel              41.00
INFO:   aacaot                2.00
INFO:   videoframerate        25.00
INFO:   audiosamplerate       24000.00
INFO:   audiochannels         2.00
INFO: trackinfo:
INFO:   length                42776000.00
INFO:   timescale             25000.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            avc1
INFO:   length                41067520.00
INFO:   timescale             24000.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            mp4a
570524.786 kB / 1711.10 sec (99.9%)
Download complete
```

Any ideas?

---

### Post by Cheesemill on 2013-01-09
What's the output of:
```
get_iplayer --prefs-show
```

---

### Post by phil_elvey on 2013-01-09
Unfortunately I've tried adding those prefs for modes there too with no result.  At current --show-prefs output:
```
Options in '/home/phil/.get_iplayer/options'
	modes = flashvhigh,flashhigh,flashstd,flashaac,flashaacstd,flashaudio,realaudio,wma
```

I've rebooted also just to be sure, but still no result.  If I were to log this "bug" with the devs, what is the best way to do that do you think?

---

### Post by Cheesemill on 2013-01-09
The get_iplayer mailing list would be the best place to ask questions and report bugs.

[http://lists.infradead.org/mailman/listinfo/get_iplayer](http://lists.infradead.org/mailman/listinfo/get_iplayer)

---

### Post by phil_elvey on 2013-01-09
Cool, I've sent a request to the mailing list.

TBH it's not that bigger deal, just annoying me that it's not doing what it should!

Thanks for your prompt replies, much appreciated

Cheers

---

