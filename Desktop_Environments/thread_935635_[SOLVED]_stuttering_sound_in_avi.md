---
title: "[SOLVED] stuttering sound in avi"
date: 2008-10-01
forum: Desktop Environments
---

### Post by dgermann on 2008-10-01
Hi--

Got a new Canon A580 camera and the sound it produces in videos cuts in and out--it sounds to me like a loose microphone cable causing crackles to be recorded.

But here's the weird part--I can play the file on my Ubuntu 8.04.1 box 6 times in a row and each time, the crackles will appear in a different place! In one 24 second clip, it will crackle 7 times the first time I play it, 4 the next, 6 the next, 6 the next, 5 the next, etc. Sometimes in the same places, sometimes not.

I have sent the camera back to Canon for repairs twice on this, along with a couple video samples. They apparently cannot hear the problem on their end, even playing on a computer and listening with earphones. The second time they replaced the "pcb assembly," whatever that is.

So I am thinking it is not a camera issue. I have even tested uploading the file to my computer from the camera using different cables. So I wonder if it is something where the computer's audio playback is not keeping up with the video and skips ahead.

Now I have another camera, a Polaroid PDC 5080, and the sound playback there is flawless. (But it makes poor indoor still pictures, so I don't like that camera!) Both cameras produce .avi files.

Is there a way to get good quality sound out of these files?

Thanks!

---

### Post by olejorgen on 2008-10-02
Try playing the file with mplayer in a terminal. Observe the output.
1. What is the first percentage number? (video decoding cpu usage)
```
A:  65.9 V:  65.9 A-V: -0.001 ct: -0.002 1581/1581 **31%**  1%  1.5% 2 0
```
2. Try combinations of mplayer -framedrop -cache 2000 -ao <from list>
```
mplayer -ao help
```

Post the output from:
```

mplayer -identify -frames 0 FILE
```

---

### Post by dgermann on 2008-10-02
olejorgen--

Thank you very much, olejorgen!

I may not be understanding all that you are suggesting here, but this is what I did.

However, running the clips in mplayer rather than totem gave me clean playbacks in all the avi files I tried. So maybe that is as far as I need to go. But perhaps the output below will tell you otherwise:

1. I ran this command and could not stop it fast enough to get the very first output from this command. So here is one from when it completed:

```
$ mplayer mvi_0048.avi 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E4400  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mvi_0048.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  640x480  24bpp  20.000 fps  5887.0 kbps (718.6 kbyte/s)
Clip info:
 Digitization Time: Fri Aug 29 19:25:18 2008

 Software: CanonMVI06
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 355.
[VO_XV] Could not grab port 356.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11024 Hz, 1 ch, u8, 88.2 kbit/100.00% (ratio: 11024->11024)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 11024Hz 1ch u8 (1 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x8934890]SwScaler: BICUBIC scaler, from yuv422p to yuv420p using MMX2
[swscaler @ 0x8934890]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x8934890]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x8934890]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x8934890]SwScaler: 640x480 -> 640x480
VO: [xv] 640x480 => 640x480 Planar YV12 
A:  15.6 V:  15.7 A-V: -0.143 ct: -0.015 315/315 10%  6%  0.3% 64 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  49.7 V:  49.7 A-V: -0.039 ct:  0.009 995/995 10%  6%  0.3% 158 0 
GNOME screensaver enabled

Exiting... (End of file)

```

2. I did not do this, since mplayer seemed to play the clips without trouble.

3. Here is the output of this command:

```
$ mplayer -identify -frames 0 mvi_0048.avi 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E4400  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mvi_0048.avi.
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  640x480  24bpp  20.000 fps  5887.0 kbps (718.6 kbyte/s)
Clip info:
 Digitization Time: Fri Aug 29 19:25:18 2008

ID_CLIP_INFO_NAME0=Digitization Time
ID_CLIP_INFO_VALUE0=Fri Aug 29 19:25:18 2008

 Software: CanonMVI06
ID_CLIP_INFO_NAME1=Software
ID_CLIP_INFO_VALUE1=CanonMVI06
ID_CLIP_INFO_N=2
ID_FILENAME=mvi_0048.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=MJPG
ID_VIDEO_BITRATE=5887040
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=20.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=1
ID_AUDIO_BITRATE=88192
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=0.05
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 355.
[VO_XV] Could not grab port 356.
[VO_XV] Could not grab port 357.
[VO_XV] Could not grab port 358.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
ID_VIDEO_CODEC=ffmjpeg
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11024 Hz, 1 ch, u8, 88.2 kbit/100.00% (ratio: 11024->11024)
ID_AUDIO_BITRATE=88192
ID_AUDIO_RATE=11024
ID_AUDIO_NCH=1
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 11024Hz 1ch u8 (1 bytes per sample)
ID_AUDIO_CODEC=pcm
Starting playback...


Exiting... (End of file)

```

It should be pretty obvious that I don't know anything about movies and sound, so what do you see here that I'm missing? Other than figure out how to make mplayer the default movie player?

Thanks, olejorgen!

---

### Post by olejorgen on 2008-10-02
No problem. I suspected it to have something to do with the sample rate. I had a somewhat similar problem with mocp, and I think the solution was to force the samplerate to 48000.

I'm not sure how you do that in totem though. Anyway, mplayer is so much better than totem :)

Btw: It does not seem like your system is to slow. (despise mplayer saying so. It sometimes does at the end of a file)

I think you need to right-click a .avi file -> properties -> open with -> add and select mplayer as the default application. I would recommend adding mplayer, not gmplayer. The gui is pretty bad. (It's a while since I've used gnome, so I don't know the exact details)

EDIT: if you want to try finding a fix for totem, search for totem samplerate pcm (something that describes the sound)

---

### Post by dgermann on 2008-10-04
olejorgen--

Thank you much.

What do you mean, and what does the note mean, that my system is too slow? The system is only about 9 months old, dual core processor, and so I would expect that most normal things (like video clips made on a simple camera) I try to run on it will run. Or does this simply mean that I need to make a change in some setting on mplayer?

(If you're so inclined to tutor the uneducated!)

Thanks, olejorgen!

---

### Post by olejorgen on 2008-10-04
If the message only showed right before the movie ended, it's notthing to worry about. Mplayer does that sometimes on my system too. With that system you should be able to play anything

---

### Post by dgermann on 2008-10-05
olejorgen--

Thank you very much for helping me with this!

---

