---
title: "Converting DiVX files to PSP readable format"
date: 2006-01-16
forum: Desktop Environments
---

### Post by fizgigg on 2006-01-16
Hey all,

Can anyone help me figure out how to convert DiVX video files to a PSP readable  video format?  I have tried using ffmpeg, but this is what I get everytime I try:

ffmpeg -i copy.avi -f psp /home/fizgigg/copy.avi

ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, avi, from 'copy.avi':
  Duration: 00:17:02.8, start: 0.000000, bitrate: 1186 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, 23.98 fps
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Output #0, psp, to '/home/fizgigg/copy.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, 23.98 fps, q=2-31, 200 kb/s
  Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0x8333448]removing common factors from framerate
Unsupported codec for output stream #0.1

Thanks in advance!

Fizgigg

---

### Post by jyona on 2006-01-16
I was also looking for a way to convert movies (not just DivX) to PSP format and found this website:

[http://www.engadget.com/2004/12/21/how-to-get-videos-and-dvds-onto-your-sony-playstation-portable/](http://www.engadget.com/2004/12/21/how-to-get-videos-and-dvds-onto-your-sony-playstation-portable/)

It's an article with a how-to on a way to do this, unfortunately the software it suggests is written for Windows (although it is free :) ) - I still have a Windows partition on my machine, and so installed the program (3GP Converter), followed the instructions and was able to convert and watch the file on my PSP with no problem.

I would suggest, if you want to try this in Ubuntu, to install wine (through apt-get or Synaptic) and run 3GP Converter through wine and see if this works. I haven't tried this yet, but will later when I get the chance and will post the results here when I can.

Hope it works for you-

---

### Post by jyona on 2006-01-16
Alright, bad news, my suggestion above is not gonna work, or at least I don't know a workaround to make it work.:(  The software in question (3GP Converter) apparently doesn't support file output to ext2/ext3 (one of the file systems Linux uses). I've tried changing the output settings to write directly onto the windows partition, but that hasn't been working.

Sorry I couldn't be of any help. If I come across anything else, I'll let you know.

---

### Post by fizgigg on 2006-01-17
Thanks for the suggestion jyona!  I also have a duel boot system, but mostly for games.  I think I will give this a try for now, but I would love to be able to do this with out a reboot.

Thanks again!

Fizgigg

---

