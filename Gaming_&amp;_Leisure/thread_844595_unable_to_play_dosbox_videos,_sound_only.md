---
title: "unable to play dosbox videos, sound only"
date: 2008-06-29
forum: Gaming &amp; Leisure
---

### Post by TurboFreak on 2008-06-29
Hi,
i recently installed DOSBox on hardy and captured some videos but i can't watch them, only the sound is playing.
(Same problem on my Desktop and Laptop PC)
Though, i was able to watch them on Windows with the ZMBV-Codec installed, that comes with DOSBox there. So they were captured correctly.
In the Windows version of DOSBox there's a Readme file to the ZMBV-Codec reading:

To play the recorded movie, you need a movie player which can handle the
ZMBV codec. MS Windows users can find this codec in the start menu entry of
DOSBox. Users of Linux and other OSes should look for a movie player that
uses the ffmpeg libary (you may need to update or ask your distribution to
upgrade).

So i looked for a player which supports ffmpeg.
On this page [http://de.wikipedia.org/wiki/FFmpeg](http://de.wikipedia.org/wiki/FFmpeg) (it's German) i found, that VLC does.
But trying to play the videos with VLC fails, too.

I also tried installing ffmpeg like described here: [http://wiki.ubuntuusers.de/FFmpeg](http://wiki.ubuntuusers.de/FFmpeg)
```
sudo apt-get install ffmpeg
sudo apt-get install libavformat-dev
sudo apt-get install libavcodec-dev
```
(Don't even know exactly which package i need. Tried these three.)

But the videos won't play.
Can anyone help me, please?

---

### Post by TurboFreak on 2008-06-30
OK, found out that MPlayer can play them.
Problem solved.

---

