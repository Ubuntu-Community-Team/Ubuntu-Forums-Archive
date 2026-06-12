---
title: "Encoding Dvd Using a codec compatible with standalone Dvd player"
date: 2006-07-26
forum: Desktop Environments
---

### Post by tabetan on 2006-07-26
I have kubuntu i386, running on an amd64 processor.

Hi, I converted my dvd movie using the lavc codec, but when I played it over my standalone dvd player it didn't work, saying "no codec to read this video". 
My target is to convert a movie and being able to play it in my standalone dvd player which can only read dvd and divx movies.
So I thought to use the divx codec but when I open acid rip, I can't see the Divx codec from the list of codecs.

Knowing that acid uses mencoder, I ran the command: 
mencoder -ovc help
and this was the output:

[FONT="Courier New"][B]MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 0)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, currently only AVID is supported.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding


Exiting... (error parsing cmdline)[/B]
[/FONT]

I can't see the divx codec.

I have got these libraries installed on my system:
[FONT="Courier New"][B]
libdivxdecore0-binary
libdivxencore0-binary[/B][/FONT]

If there's anyone of you that could help I would really appreciate it.

---

### Post by RAOF on 2006-07-26
Divx is MPEG4 video.  Specifically, MPEG4 ASP video, possibly with some limitations on various options (I'm not sure), and with a fourcc of "DIVX".  I'm not quite sure how mplayer interfaces with ffmpeg (the project in which libavcodec is developed), but the sort of options you're after are "-vcodec mpeg4 -vtag 'DIVX'".

Alternatively, you could probably pass the "-target dvd" to mplayer (or equivalent - that's the ffmpeg option).  **Guaranteed** to produce DVD-player readable MPEG2 audio/video :)

---

### Post by tabetan on 2006-07-26
I searched on the web a little more and it seems like the only way is to changing the fourcc from 'FMP4' to 'DIVX' but:
how do I do this?
Can I do this from acidrip?

thank you.
Tabetan

---

### Post by RAOF on 2006-07-26
A brief check of "man mencoder" says that you want to add the option "-ffourcc DIVX".

---

### Post by Iesos on 2006-07-27
I found this:

"Here's an example that will create a DivX AVI using lavc to create mpeg4 for video, and your audio to mp2. mpeg4 and mp2 are the default codecs used when no options are passed."

```
mencoder <filename.avi> -ovc lavc -oac lavc -ffourcc DX50 -o <output.avi>
```

I found it at: [http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

Good luck.

---

### Post by gingermark on 2006-07-27
It should probably be noted that most files encoded with xvid will play on DivX players. Not guaranteed, but very likely to work.

---

