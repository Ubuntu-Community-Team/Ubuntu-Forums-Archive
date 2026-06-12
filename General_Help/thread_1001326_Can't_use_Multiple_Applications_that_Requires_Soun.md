---
title: "Can't use Multiple Applications that Requires Sound = Mplayer/Totem"
date: 2008-12-03
forum: General Help
---

### Post by Sugi on 2008-12-03
I am having a lot issues with mplayer and totem playing movies.  If I open any other programs before IE Teamspeak, wine, or opera Mplayer freezes and totem plays all videos in slow motion.  But if I only open mplayer or totem they play in normal speed.  I have been able to play DVD through both Totem and mplayer along with avis.  But Totem has this shattering effect to the video (I think that's what you call that, shattering).  Any idea on how to fix this problem.

BTW, mplayer -vo x11 dvd:// (does not work either)

The terminal output with teamspeak was open first and then tried mplayer with dvd movie.

```
mplayer dvd://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
 
Playing dvd://.
There are 1 titles on this DVD.
There are 30 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: fr aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9100.0 kbps (1137.5 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
GNOME screensaver enabled.085 ct: -0.004   6/  6 ??% ??% ??,?% 0 0 
 
Exiting... (Quit)
```

Ubuntu Hard Heron
Mplayer
Totem
i386

Sugi

---

### Post by AliTabuger7 on 2008-12-03
I'm not a sound expert, but this is generally due to using integrated audio.

What I usually do is find a (cheap) soundcard laying around somewhere and use that.

There is probably something better that you could do with ALSA, OSS, or Pulseaudio, but I cannot help you very well in that area.

---

### Post by Sugi on 2008-12-03
Oh, I forgot to add.  If Mplayer or Totem is open nothing else can get sound.  I am using a laptop. :-/

Sugi

---

### Post by Sugi on 2008-12-04
Bump

---

### Post by Sugi on 2008-12-05
Bump

---

### Post by Sugi on 2008-12-07
Bump

---

### Post by Sugi on 2008-12-08
bv|\/|p

---

### Post by psyke83 on 2008-12-08
You need to configure PulseAudio properly.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

