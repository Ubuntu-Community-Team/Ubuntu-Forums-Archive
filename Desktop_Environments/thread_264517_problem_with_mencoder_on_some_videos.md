---
title: "problem with mencoder on some videos"
date: 2006-09-24
forum: Desktop Environments
---

### Post by rainbowjoshua on 2006-09-24
Okay, so I've ripped a bunch of DVDs just fine.  I rip them with with dvd::rip and it works great, and usually, I can go through the entire encoding process with it, and it works great.  

However, with some DVDs, nearly half of the ones I try, I can rip the movie with dvd::rip, but not encode it.  When I bring up the clip and zoon dialog, the frame just doesn't come up, like it can't find the movie.  I don't know why.

So what I usually do when that happens is to then fire up acidrip and point it to the VOBs in the rip directory and set the settings and encode this way (after concatenating all the VOBs together into one file so I don't have to encode six separate files and merge them together after).

For some reason, with some movies, acidrip has not worked.  And since it's just a frontend for mencoder, I will rephrase and say that for some reason mencoder isn't working.  Here is what it returns when it doesn't work.  But for some reason, it doens't do them with every DVD, just some of them and I haven't figured out what the difference between the ones that work and the ones that don't are.

```

joshua@alvin:/mnt/sda/rip/unitedflight93/vob/001$ mencoder \/mnt\/sda\/rip\/snowwalker\/vob\/001\/sw\.vob  -alang English   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts abr:br=128  -ovc xvid -xvidencopts :bitrate=1307:pass=1 -vf pp=de,crop=704:464:10:10   -ofps 24000/1001 -o "/dev/null"
MEncoder dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags: Type: 8 MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE

86 audio & 200 video codecs
File not found: 'frameno.avi'
Failed to open frameno.avi
success: format: 0  data: 0x0 - 0x1da60800
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  4800.0 kbps (600.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dts' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to DTS, 768000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 768.0 kbit/50.00% (ratio: 96000->192000)
Selected audio codec: [hwdts] afm:hwac3 (DTS through S/PDIF)
==========================================================================
xvid: using library version 1.0.3 (build xvid-1.0.3)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [crop w=704 h=464 x=10 y=10]
Crop: 704 x 464, 10 ; 10
Opening video filter: [pp=de]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred csp: Mpeg PES)
[PP] Using external postprocessing filter, max q = 6.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/ac3 -> 0Hz/0ch/??...
MP3 audio selected
Building audio filter chain for 48000Hz/2ch/ac3 -> 48000Hz/2ch/s16le...
[format] Sample format big-endian AC3 not yet supported
[libaf] Reinitialization did not work, audio filter 'format' returned error code -2
Couldn't find matching filter/ao format!

Exiting...
joshua@alvin:/mnt/sda/rip/unitedflight93/vob/001$ mencoder \/mnt\/sda\/rip\/snowwalker\/vob\/001\/sw\.vob  -alang English   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts abr:br=128  -ovc xvid -xvidencopts :bitrate=1307:pass=2 -vf pp=de,crop=704:464:10:10   -ofps 24000/1001 -o "/home/joshua/snowwalker.avi"
MEncoder dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags: Type: 8 MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE

86 audio & 200 video codecs
File not found: 'frameno.avi'
Failed to open frameno.avi
success: format: 0  data: 0x0 - 0x1da60800
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  4800.0 kbps (600.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dts' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to DTS, 768000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 768.0 kbit/50.00% (ratio: 96000->192000)
Selected audio codec: [hwdts] afm:hwac3 (DTS through S/PDIF)
==========================================================================
xvid: using library version 1.0.3 (build xvid-1.0.3)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [crop w=704 h=464 x=10 y=10]
Crop: 704 x 464, 10 ; 10
Opening video filter: [pp=de]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred csp: Mpeg PES)
[PP] Using external postprocessing filter, max q = 6.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/ac3 -> 0Hz/0ch/??...
MP3 audio selected
Building audio filter chain for 48000Hz/2ch/ac3 -> 48000Hz/2ch/s16le...
[format] Sample format big-endian AC3 not yet supported
[libaf] Reinitialization did not work, audio filter 'format' returned error code -2
Couldn't find matching filter/ao format!

Exiting...
joshua@alvin:/mnt/sda/rip/unitedflight93/vob/001$



```

Any help is much appreciated!
Thanks!
Joshua

---

