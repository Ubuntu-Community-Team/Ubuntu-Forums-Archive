---
title: "Video editing crash"
date: 2005-12-08
forum: General Help
---

### Post by Zalbor on 2005-12-08
I have a video file in .avi format, and I tried to edit it with Kino, but the program crashes just by clicking on the file in the "open" dialog. Reading previous threads here, I installed automatix to find codecs. Kino still crashes and automatix messed up synaptic (though I think that's fixed now).

How can I edit the file? I need to cut it into shorter clips. Any help will be welcome, thank you.

---

### Post by 23meg on 2005-12-08
Is it a DV avi file captured from a camcorder? If not, do you know what codec it's compressed with?

---

### Post by Zalbor on 2005-12-08
I downloaded it, no idea what a DV file is. But it's compressed with xvid.

---

### Post by claydoh on 2005-12-08
kino 0.75 as available in ubuntu does not import these files, they need to be DV files from a dv camcorder. However, the latest (0.81) version will try and import files using ffmppeg and/or mencoder. you can install ffmpeg and mencoder which are available in univers/multiverse. Unfortunately this latest version of kino does not look to be available for debian/ubuntu yet.

I believe the command to do this is:
ffmpeg -i your.avi -vcodec copy -ac 2 -ar 48000 your-converted-filename.dv
I don't know if there is a gui program available via synaptic/apt to do this.

One possible thing to search in the forums for is an editor called avidemux, that may be able to open your files.

---

### Post by Zalbor on 2005-12-08
Thanks! :)
I currently found a way to do what I need in windows, but I'll try your suggestion when I have time, for future operations.

---

### Post by freedomjazzdance on 2005-12-30
ok but i wanna convert a .mpg to a .dv because my camera saves them as .mpg's

i tried what you said and i got an error 

lee@thepurpletongues:~/movie$ ffmpeg -i chris.MPG -vcodec copy -ac 2 -ar 48000 movie.dv ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, mpeg, from 'chris.MPG':
  Duration: 00:00:37.0, start: 0.083333, bitrate: 2358 kb/s
  Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 320x240, 24.00 fps, 104857 kb/s
  Stream #0.1[0x1c0]: Audio: mp2, 32000 Hz, mono, 96 kb/s
Output #0, dv, to 'movie.dv':
  Stream #0.0: Video: mpeg1video, 320x240, 24.00 fps, q=2-31, 104857 kb/s
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[dv @ 0x82c5740]Can't initialize DV format!
Make sure that you supply exactly two streams:
     video: 25fps or 29.97fps, audio: 2ch/48Khz/PCM
Could not write header for output file #0 (incorrect codec parameters ?)
lee@thepurpletongues:~/movie$

---

