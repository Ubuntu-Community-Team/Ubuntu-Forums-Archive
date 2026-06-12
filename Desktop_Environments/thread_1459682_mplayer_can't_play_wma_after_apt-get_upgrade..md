---
title: "mplayer can't play wma after apt-get upgrade."
date: 2010-04-21
forum: Desktop Environments
---

### Post by MgFrobozz on 2010-04-21
While I was running apt-get upgrade about a day ago, I was listening to a wma file using mplayer. About 5 minutes after the upgrade, I stopped mplayer and started it on another wma file, and got the error report below, indicating it wasn't able to find the codec support. The upgrade replaced several media/audio-related libraries. 

Anyone know which package now contains wmadmod.dll? Any suggestions on how to fix my wma playback would be most appreciated. 

Reported during the upgrade:
```

> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libavcodec52 libavformat52 libavutil49 libpostproc51 libswscale0
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,016kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic-updates/main libavutil49 4:0.5+svn20090706-2ubuntu2.1 [92.7kB]
Get:2 http://us.archive.ubuntu.com karmic-updates/main libavcodec52 4:0.5+svn20090706-2ubuntu2.1 [3,973kB]
Get:3 http://us.archive.ubuntu.com karmic-updates/main libavformat52 4:0.5+svn20090706-2ubuntu2.1 [708kB]
Get:4 http://us.archive.ubuntu.com karmic-updates/main libpostproc51 4:0.5+svn20090706-2ubuntu2.1 [69.8kB]
Get:5 http://us.archive.ubuntu.com karmic-updates/main libswscale0 4:0.5+svn20090706-2ubuntu2.1 [172kB]
Fetched 5,016kB in 4s (1,197kB/s)  
(Reading database ... 219938 files and directories currently installed.)
Preparing to replace libavutil49 4:0.5+svn20090706-2ubuntu2 (using .../libavutil49_4%3a0.5+svn20090706-2ubuntu2.1_i386.deb) ...
Unpacking replacement libavutil49 ...
Preparing to replace libavcodec52 4:0.5+svn20090706-2ubuntu2 (using .../libavcodec52_4%3a0.5+svn20090706-2ubuntu2.1_i386.deb) ...
Unpacking replacement libavcodec52 ...
Preparing to replace libavformat52 4:0.5+svn20090706-2ubuntu2 (using .../libavformat52_4%3a0.5+svn20090706-2ubuntu2.1_i386.deb) ...
Unpacking replacement libavformat52 ...
Preparing to replace libpostproc51 4:0.5+svn20090706-2ubuntu2 (using .../libpostproc51_4%3a0.5+svn20090706-2ubuntu2.1_i386.deb) ...
Unpacking replacement libpostproc51 ...
Preparing to replace libswscale0 4:0.5+svn20090706-2ubuntu2 (using .../libswscale0_4%3a0.5+svn20090706-2ubuntu2.1_i386.deb) ...
Unpacking replacement libswscale0 ...
Setting up libavutil49 (4:0.5+svn20090706-2ubuntu2.1) ...

Setting up libavcodec52 (4:0.5+svn20090706-2ubuntu2.1) ...

Setting up libavformat52 (4:0.5+svn20090706-2ubuntu2.1) ...

Setting up libpostproc51 (4:0.5+svn20090706-2ubuntu2.1) ...

Setting up libswscale0 (4:0.5+svn20090706-2ubuntu2.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

The error message from mplayer (this is an audio-only file):
```

> mplayer kbps_64_2010_04_17.wma
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing kbps_64_2010_04_17.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[wmav2 @ 0x9f3e570]codec type or id mismatches
Could not open codec.
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wmadmod.dll, /usr/lib/codecs/wmadmod.dll, /usr/lib/win32/wmadmod.dll, /usr/local/lib/win32/wmadmod.dll
IMediaObject ERROR: 0x840d7d1  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wmadmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [acm] Win32/ACM decoders
Loading codec DLL: 'divxa32.acm'
Win32 LoadLibrary failed to load: divxa32.acm, /usr/lib/codecs/divxa32.acm, /usr/lib/win32/divxa32.acm, /usr/local/lib/win32/divxa32.acm
Can't open library divxa32.acm
ACM_Decoder: Unappropriate audio format
Could not load/initialize Win32/ACM audio codec (missing DLL file?).
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x161.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video

```

```

> cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

```

---

### Post by andrew.46 on 2010-04-22
Hi MgFrobozz,

Can you post this troublesome file somewhere?

Andrew

---

### Post by SunnyBUG on 2010-04-22
See this bug:

[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/567913](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/567913)

---

### Post by MgFrobozz on 2010-04-22
Thanks, SunnyBUG ... I'll wait for MarcD's fix.

---

### Post by MgFrobozz on 2010-04-26
WMA playback is working again in mplayer after 'sudo apt-get upgrade' today (details below). Thanks ... I can listen to mms://wm-live.abacast.com/classical899-classical899-64 again!

```

Preparing to replace libavutil49 4:0.5+svn20090706-2ubuntu2.1 (using .../libavutil49_4%3a0.5+svn20090706-2ubuntu2.2_i386.deb) ...
Unpacking replacement libavutil49 ...
Preparing to replace libavcodec52 4:0.5+svn20090706-2ubuntu2.1 (using .../libavcodec52_4%3a0.5+svn20090706-2ubuntu2.2_i386.deb) ...
Unpacking replacement libavcodec52 ...
Preparing to replace libavformat52 4:0.5+svn20090706-2ubuntu2.1 (using .../libavformat52_4%3a0.5+svn20090706-2ubuntu2.2_i386.deb) ...
Unpacking replacement libavformat52 ...
Preparing to replace libavdevice52 4:0.5+svn20090706-2ubuntu2.1 (using .../libavdevice52_4%3a0.5+svn20090706-2ubuntu2.2_i386.deb) ...
Unpacking replacement libavdevice52 ...
Preparing to replace libavfilter0 4:0.5+svn20090706-2ubuntu2.1 (using .../libavfilter0_4%3a0.5+svn20090706-2ubuntu2.2_i386.deb) ...
Unpacking replacement libavfilter0 ...
Preparing to replace libpostproc51 4:0.5+svn20090706-2ubuntu2.1 (using .../libpostproc51_4%3a0.5+svn20090706-2ubuntu2.2_i386.deb) ...
Unpacking replacement libpostproc51 ...
Preparing to replace libswscale0 4:0.5+svn20090706-2ubuntu2.1 (using .../libswscale0_4%3a0.5+svn20090706-2ubuntu2.2_i386.deb) ...
Unpacking replacement libswscale0 ...
Preparing to replace ffmpeg 4:0.5+svn20090706-2ubuntu2.1 (using .../ffmpeg_4%3a0.5+svn20090706-2ubuntu2.2_i386.deb) ...

```

---

