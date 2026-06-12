---
title: "video w/ bigger res than my screen"
date: 2006-07-11
forum: Desktop Environments
---

### Post by masnevets on 2006-07-11
Hi, I am trying to play a .mp4 file that is 1280x720, and my screen resolution is 1024x768. There seems to be a problem getting this to work in Linux (I can play the file in Windows). When I load it with mplayer, I get the following:

```
mplayer \[Triad\]_5cm_teaser.mp4
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf doesn't look like a font description, ignoring.
Cannot load font: /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
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
Playing [Triad]_5cm_teaser.mp4.
Quicktime/MOV file format detected.
--------------
MOV track #0: 91 chunks, 1089 samples
MOV: AVC decoder configuration record atom (47)!
MOV: Found unknown movie atom btrt (20)!
Image size: 1280 x 720 (24 bpp)
Display size: 1280 x 720
Fourcc: avc1  Codec: ''
--------------
MOV track #1: 99 chunks, 982 samples
Audio bits: 16  chans: 2  rate: 22050
MOV: Found MPEG4 audio Elementary Stream Descriptor atom (44)!
Fourcc: mp4a
--------------
MOV: longest streams: A: #1 (982 samples)  V: #0 (1089 samples)
VIDEO:  [avc1]  1280x720  24bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 129.1 kbit/9.15% (ratio: 16139->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12
aspect: Warning: no suitable new res found!
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed
```

I've also tried VLC and the default movie player in Ubuntu, but they give the same problem. The file will load for a brief moment, then close with an error message. I also tried manually resizing the video output with 

mplayer -x 1024 -y 576

but this also did not work. I have also been able to play other .mp4 files, so it shouldn't be a problem with the codec. I've seen a similar thread with this problem, but the fix there didn't help:

[http://ubuntuforums.org/showthread.php?t=116196](http://ubuntuforums.org/showthread.php?t=116196) (post #4)

Thanks for your help,
Steven

---

### Post by Bossieman on 2006-07-11
I have the same problem, cant playback movies with higher resolution than my desktop.

---

### Post by psyke83 on 2006-07-11
Hi,

The problem is that Xvideo cannot allocate enough memory to display your movie. Try appending "-vo x11" to mplayer, i.e.:
```
mplayer \[Triad\]_5cm_teaser.mp4 -vo x11
```What graphics card have you got? If you have an Intel integrated chipset for example, you can solve the problem by adding this to  'Section "Device"' in /etc/X11/xorg.conf:```
Option "LinearAlloc" "6144"
```From "man i810":
> Option "LinearAlloc" "integer"
    Allows more memory for the offscreen allocator. This usually helps in situations where HDTV movies are required to play but not enough offscreen memory is usually available. Set this to 6144 for upto 1920x1080 HDTV support. Default 0KB (off).If your graphics card supports a similar feature, then you can play larger movies without resorting to X11 output.

---

### Post by masnevets on 2006-07-11
Thanks for the quick response. Editing xorg.conf did not work, but using -vo x11 did. For reference, here's my entry:

```
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option 		"LinearAlloc" "6144"
EndSection
```

One last thing: I think when I view it, it's cutting off the sides because when I go to fullscreen, it fills the screen, but if the aspect is kept, it should have black bars on top and bottom.

And note for anyone else: when I originally did this, it was lagging like crazy, but that was because I had framedropping on. Turning it off worked wonders.

-Steven

---

### Post by psyke83 on 2006-07-11
Hi masnevets,

You've edited xorg.conf properly, but the problem may be that your driver is too old. I have an updated driver from a custom repository that's needed to make Compiz work on my card. See: [http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068)

If you don't want to bother with that stuff, just keep using mplayer's x11 output with larger videos - but as you saw, performance is bad. Check out
```
mplayer -vo help
```..and experiment with different output types such as -vo gl or -vo gl2, maybe they'll work better :)

Oh, about your video clipping trouble: mplayer doesn't zoom (or scale?) x11 output by default, so you need to edit /etc/mplayer/mplayer.conf and uncomment or insert "zoom=yes" somewhere. Hopefully that will also downscale a large video properly.

---

