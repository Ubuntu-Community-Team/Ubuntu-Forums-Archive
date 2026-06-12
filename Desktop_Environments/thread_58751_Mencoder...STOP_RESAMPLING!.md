---
title: "Mencoder...STOP RESAMPLING!"
date: 2005-08-21
forum: Desktop Environments
---

### Post by seethru on 2005-08-21
In my quest to eliminate any need to boot windows, I've been trying to get mencoder to rip dvd -> xvid the way I like it. ac3 5.1 audio, 1.4gb file. The video that has been coming out is looking GREAT, however, choosing "copy" in acidrip (or the command line for that matter) causes mencoder to RESAMPLE the ac3 file to 2 channels!

Does anyone know why it's doing this?

edit: The lines in the terminal regarding the audio.

```
Opening audio decoder: [liba52] AC3 decoding with liba52
AC3: 5.1 (3f+2r+lfe)  48000 Hz  448.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 56000->192000 (448.0 kbit)
Selected audio codec: [a52] afm:liba52 (AC3-liba52)
```

---

### Post by trigg on 2005-08-21
Try this:

```

  -channels 6 -oac lavc -lavcopts acodec=ac3:abitrate=384

```

It's from the MPlayer documentation on the MPlayer website - more useful info here:

[http://www.mplayerhq.hu/~diego/DOCS/HTML/en/](http://www.mplayerhq.hu/~diego/DOCS/HTML/en/)

---

### Post by seethru on 2005-08-22
[QUOTE=trigg]Try this:

```

  -channels 6 -oac lavc -lavcopts acodec=ac3:abitrate=384

```

It's from the MPlayer documentation on the MPlayer website - more useful info here:

[http://www.mplayerhq.hu/~diego/DOCS/HTML/en/](http://www.mplayerhq.hu/~diego/DOCS/HTML/en/)[/QUOTE]
 ty, that did do the trick, even with "copy." I remember reading -channels 6 but thinking to myself "copying shouldn't need that." I was wrong, lol.

I'M FREEEEEEEEEEE

---

### Post by trigg on 2005-08-23
no problem -- glad it helped

---

### Post by totus on 2008-01-30
I am having the same problem, however when I use the -channels 6 flag I get the following error.  Any ideas on how to fix this?

Script:

```
#!/bin/sh
echo "***********************************************************"
echo "Automated script created by AcidRip - http://acidrip.sf.net"
echo "***********************************************************"
unlink frameno.avi 2> /dev/null
/usr/local/bin/mencoder dvd://1 -dvd-device /archives/dvds/OFFICE_SPACE/  -alang English   -info srcform="
DVD ripped by acidrip.sf.net" -channels 6 -oac copy  -ovc xvid -xvidencopts bitrate=2526 pass=1     -o "/d
ev/null"
```

Execution:

troy@palms:~$ ./acidrip.sh
***********************************************************
Automated script created by AcidRip - [http://acidrip.sf.net](http://acidrip.sf.net)
***********************************************************
MEncoder 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 3.00GHz (Family: 15, Model: 6, Stepping: 4)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

There are 3 titles on this DVD.
There are 29 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: es
subtitle ( sid ): 1 language: en
number of subtitles on disk: 2
success: format: 2  data: 0x0 - 0xf8ec3800
No matching DVD audio language found!
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
[COLOR="Red"]Unimplemented resampler for mode 0xA -> 6 channels conversion - Contact MPlayer developers!
Unimplemented resampler for mode 0xA -> 5 channels conversion - Contact MPlayer developers!
Unimplemented resampler for mode 0xA -> 4 channels conversion - Contact MPlayer developers!
Unimplemented resampler for mode 0xA -> 3 channels conversion - Contact MPlayer developers![/COLOR]
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
xvid: using library version 1.1.3 (build xvid-1.1.3)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
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
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: XviD (720x480 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=720x540, sampled=720x480
xvid: CBR Rate Control -- bitrate=2526kbit/s
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
Pos:   0.0s      1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Writing header...
ODML: vprp aspect is 4:3.
Setting audio delay to 0.033s.
Writing header...
ODML: vprp aspect is 4:3.
Setting audio delay to 0.033s.
Writing header...2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.003 [0:0]
ODML: vprp aspect is 4:3.
Setting audio delay to 0.033s.

1 duplicate frame(s)!
Pos:   0.1s      4f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.010 [0:0]
1 duplicate frame(s)!
Pos:   0.2s      6f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.017 [0:0]

---

