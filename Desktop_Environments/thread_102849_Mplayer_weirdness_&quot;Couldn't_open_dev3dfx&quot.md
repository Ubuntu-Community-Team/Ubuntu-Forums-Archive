---
title: "Mplayer weirdness: &quot;Couldn't open /dev/3dfx&quot;"
date: 2005-12-12
forum: Desktop Environments
---

### Post by urinetrouble on 2005-12-12
Hi everyone, newbie to the forums/ubuntu, first of all I'd like to say hi. This looks like a pretty supportive community, so I'm confident you'll be able to help me out here :)

Mplayer is giving me a bizarre error. This is happening with all video files:

```

$mplayer atomicbomb.wmv
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel  (Family: 8, Stepping: 1)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.


86 audio & 200 video codecs
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Setting up LIRC support...
Playing atomicbomb.wmv.
ASF file format detected.
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm:ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
vo_mga: Couldn't open /dev/mga_vid
vo_mga: Couldn't open /dev/mga_vid
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmv9dmod.dll, /usr/lib/win32/wmv9dmod.dll, /usr/local/lib/win32/wmv9dmod.dll
IMediaObject ERROR: 0x858d3f9  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
You need to upgrade/install the binary codecs package.
Go to http://mplayerhq.hu/homepage/dload.html
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmvdmod.dll, /usr/lib/win32/wmvdmod.dll, /usr/local/lib/win32/wmvdmod.dll
IMediaObject ERROR: 0x858d3f9  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
You need to upgrade/install the binary codecs package.
Go to http://mplayerhq.hu/homepage/dload.html
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm:ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa-init: 1 soundcard found, using: default
[AO SDL] Samplerate: 22050Hz Channels: Stereo Format s16le
AO: [null] 22050Hz 2ch s16le (2 bps)
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 320 x 240 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [3dfx] 320x240 => 320x240 Planar YV12 
Couldn't open /dev/3dfx

```

Yes, the same goes for .mpg files as well with the exact same error. What makes this error extra strange is that my video card is not a 3dfx card at all. I can't say there's a spot of 3dfx in this machine at all; it's an IBM thinkpad G41with an nvidia gofx5200 in it. I'm guessing this isn't an mplayer-specific problem, because mplayer was working just fine when I was using FreeBSD on this particular machine. Anyone know what gives? This is a pretty annoying error.

---

### Post by RAOF on 2005-12-13
You probably want to change the mplayer video out options.  Looks like it's currently set to 3dfx :)

---

### Post by urinetrouble on 2005-12-13
Gee golly, you're right. I should have spotted that faster :oops:

Just for convenience's sake, do you know how I would go about doing that?

Also, for curiosity's sake, why in the world is it set like that, anyways? That's... odd.

Thanks! :)

---

### Post by RAOF on 2005-12-13
I don't use mplayer myself, but I believe that you can change the video-out options by right-clicking, selecting "preferences", and going to the video options page.  XV is probably the driver you want.

---

### Post by urinetrouble on 2005-12-13
This only helps for gmplayer. It still works in gmplayer, but it's still not working with the cli-induced version, weirdly enough. Any tips?

Plus, where are my windows media video codecs? You'd think that they'd be installed by default. Is there a package I can apt-get for this, or do I have to dork around with this particular problem the HARD way ;)?

Thanks again.

---

### Post by RAOF on 2005-12-13
Why would copyright-infringing binary wmv codecs be included by default? ;)

I'd suggest searching the forums for info on the win32codecs package.  You can get it from somewhere.

---

### Post by urinetrouble on 2005-12-15
*shrug* They're ALL downloaded by default in FreeBSD ports. It's just an extra windows codec pack with wrappers. I don't really see why ubuntu can't do the same.

---

### Post by RAOF on 2005-12-15
Because they violate the licensing agreement?  Because it's illegal?  Because one of the principles of Ubuntu is "free software by default"

---

### Post by cjazz on 2005-12-15
FYI, the package you should search for is w32codecs.

---

### Post by urinetrouble on 2005-12-17
[QUOTE=cjazz]FYI, the package you should search for is w32codecs.[/QUOTE]

Under what repository?

---

