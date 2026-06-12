---
title: "Quicktime movie won't play"
date: 2006-08-11
forum: Desktop Environments
---

### Post by drpaul on 2006-08-11
There is a Quicktime movie 
[http://media.rubyonrails.org/video/rails_take2_with_sound.mov](http://media.rubyonrails.org/video/rails_take2_with_sound.mov)

on the "Ruby on Rails" site that just starts a burst of audio and then fails. Have tried both mplayer and totem; same behavior with both. Error message on terminal says it's probably a program bug. Since it happens with both programs, it's probably a problem with some common element.

Any ideas?

Paul

---

### Post by Dr. Nick on 2006-08-11
did you save it to your hd, or trying to play it in the browser?

I saved it to my hd and got sound and video with mplayer, do you have w32codecs?

---

### Post by jordilin on 2006-08-11
You need the codecs. Follow these little instructions:
[http://ubuntuos.wordpress.com/2006/08/01/howto-play-windows-media-video-wmv-in-ubuntu/](http://ubuntuos.wordpress.com/2006/08/01/howto-play-windows-media-video-wmv-in-ubuntu/)

---

### Post by drpaul on 2006-08-11
Yes the file is local.

Is the package that you suggest different from the w32codecs package that Ubuntu has in the repos?

Paul

---

### Post by Dr. Nick on 2006-08-12
no, the w32codecs package is the one I meant. It works locally for me in mplayer, but not totem or vlc.

I didnt think mplayer relied on gstreamer, but you may open synaptic and install the various gstreamer .1 plugins

---

### Post by drpaul on 2006-08-12
I tried running mplayer with the Quicktime movie again in a terminal and got this very long output. Seems like there are lots of bad things happening, but I don't know how to attack them. Help is appreciated.
> 
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 6)CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing mplaylAFdCL.
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
--------------
MOV track #0: 5411 chunks, 5876 samples
Image size: 970 x 754 (32 bpp)
Display size: 970 x 754
Fourcc: rle   Codec: 'Animation'
--------------
MOV track #1: 4013 chunks, 37081 samples
Audio bits: 16  chans: 1  rate: 44100
Audio extra header: len=76  fcc=0x77617665
MOV: Found unknown audio atom Fourcc: .mp3
--------------
MOV track #2: 2 chunks, 2 samples
Image size: 970 x 754 (32 bpp)
Display size: 970 x 754
Fourcc: rle   Codec: 'Animation'
--------------
MOV: longest streams: A: #1 (37081 samples)  V: #0 (5876 samples)
VIDEO:  [rle ]  970x754  32bpp  5.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffqtrle] vfm: ffmpeg (QuickTime Animation (RLE))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 970 x 754 (preferred colorspace: BGRA)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using BGRA as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.

SwScaler: BICUBIC scaler, from BGRA to Planar YV12 using MMX2
VO: [xv] 970x754 => 970x754 Planar YV12
alsa-space: xrun of at least 703.628 msecs. resetting stream?% 0 0
X11 error: BadAlloc (insufficient resources for operation)


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed


Paul

---

### Post by drpaul on 2006-08-12
jordilin:
I checked the dates on the files in the link you suggested, and they are all earlier than the ones that came from the link you suggested. What do you think?

paul

---

### Post by jordilin on 2006-08-12
> **drpaul said:**
> jordilin:
I checked the dates on the files in the link you suggested, and they are all earlier than the ones that came from the link you suggested. What do you think?

paul

Download the latest codecs from mplayer website in:
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
and follow the instructions pointed out in the link I gave you. Forget about the dates. 8-)

---

### Post by drpaul on 2006-08-12
Downloaded the codecs from the mplayer page, copied them over to the /usr/lib/win32 directory. Ran mplayer again and got the same results as I posted above.

Any ideas?

Paul

---

### Post by jordilin on 2006-08-12
> **drpaul said:**
> Downloaded the codecs from the mplayer page, copied them over to the /usr/lib/win32 directory. Ran mplayer again and got the same results as I posted above.

Any ideas?

Paul

What permissions has the win32 folder? do 
```
ls -ld win32
```
copy and paste it here.

---

### Post by drpaul on 2006-08-12
Here ya go

> paul@paulsbox:~$ ls -ld /usr/lib/win32
drwxr-xr-x 2 root root 8192 2006-08-12 09:18 /usr/lib/win32


---

### Post by jordilin on 2006-08-12
Permissions are not the problem, because I have the same as you.

---

### Post by elektronaut on 2007-01-04
It might be a bit late to reply, but as I just managed to watch the same video with mplayer, I guess others might still benefit. I'm not sure about the OP's problem, but I simply had to change [this](http://ubuntuforums.org/showpost.php?p=1791179&postcount=2) in the preferences of mplayer.

---

