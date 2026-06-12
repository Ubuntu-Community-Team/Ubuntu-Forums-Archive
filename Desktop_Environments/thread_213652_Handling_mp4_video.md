---
title: "Handling mp4 video"
date: 2006-07-11
forum: Desktop Environments
---

### Post by jazzgossen on 2006-07-11
I'm trying to edit a few video clips shot with a camera that gives me mp4 video. However, Kino won't import the files. Another strange problem is that when I view them in totem or gxine, for example, I only see the upper left quarter of the video. Sound works fine.

I tried to convert the files with ffmpeg. Running "ffmpeg -i in.mp4 out.mpg" gives me
```
Input #0, mov,mp4,m4a,3gp,3g2, from 'in.mp4':
  Duration: 00:00:40.7, start: 0.000000, bitrate: 1904 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, 29.97 fps
  Stream #0.1: Audio: mp4a / 0x6134706D, 48000 Hz, stereo
Output #0, mpeg, to 'out.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 640x480, 29.97 fps, q=2-31, 200 kb/s
  Stream #0.1: Audio: mp2, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86018) for input stream #0.1

```

Is there something I can install to get the mp4a codec installed?

I also tried "ffmpeg -acodec copy -i in.mp4 out.mpg". That gives me a proper (though more lossy) mpeg vide file, but without audio. After this conversion, I see all of the video, and not just the upper left part.

Is there another way to get these mp4 files into either Kino or Cinerella?

---

### Post by ironfistchamp on 2006-07-11
Apparently MPlayer supports MP4 files. I jave never tried it though. Worth a shot I suppose.

---

### Post by jazzgossen on 2006-07-12
I tried some more to convert the files with ffmpeg and mencoder, and the main problem seems to be that the programs think that the input file size is 320x240, although it's not. I tried specifying the image size with the flag "-s 640x480" to ffmpeg, and the output file was indeed magnified accordingly, but it still only showed the upper left part of the video. I wonder why. If I look at the input files in Windows, they look just fine.

---

### Post by konst88 on 2006-07-12
try installing avidemux.
it should do the work.
good luck.

---

### Post by jazzgossen on 2006-07-12
Thanks for the avidemux tip. It looks like a great program. I can run my mp4 files through it and get a nice-looking avi, where all of the video is visible.

However, I still can't import the files into Kino :(. When it tries to convert them to DV files, it just says "Failed to load media file", as before. No further explanation. I couldn't find any info on what demands Kino has on the input file, either. Perhaps I should try Cinelerra instead.

---

### Post by philippe_carlo on 2006-07-12
Take a look at [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
Lots of goodies and it may fix you problem too. Let me know.

---

### Post by mister_p_1998 on 2006-08-28
> **jazzgossen said:**
> Thanks for the avidemux tip. It looks like a great program. I can run my mp4 files through it and get a nice-looking avi, where all of the video is visible.

However, I still can't import the files into Kino :(. When it tries to convert them to DV files, it just says "Failed to load media file", as before. No further explanation. I couldn't find any info on what demands Kino has on the input file, either. Perhaps I should try Cinelerra instead.

How did you get Avidemux loading mp4's? it says unknown format when I try.

---

### Post by jazzgossen on 2006-08-28
Hmm, must be some codec that I have that you're missing, then. I didn't do anything special to avidemux, to my knowledge. libmp4v2-0, maybe? Just guessing, though.

---

### Post by dandellion on 2006-09-09
> **jazzgossen said:**
> Hmm, must be some codec that I have that you're missing, then. I didn't do anything special to avidemux, to my knowledge. libmp4v2-0, maybe? Just guessing, though.

I do have libmp4v2-0 installed, but avidemux is crashing the instant I try to open m4v file.....

---

### Post by sportman1280 on 2006-09-09
i am having similar problems.  i used automatrix, and it usually fixs it... but it isnt working for me this time around :(.  they are videos downloaded from google for the ipod. but they should still play in mp4 format.... sigh :(

---

