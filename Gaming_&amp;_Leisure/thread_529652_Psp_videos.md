---
title: "Psp videos"
date: 2007-08-19
forum: Gaming &amp; Leisure
---

### Post by try2lickurelbo on 2007-08-19
I'm trying to convert some videos for my psp, but i'm not sure what to do or use.

I found ffmpeg, and i have no idea at all how to install

Regards,
Mitch

---

### Post by drobvice on 2007-08-19
I haven't tried it but avidemux has output settings for psp and psp h.264.

---

### Post by jacob01 on 2007-08-19
how i did it was with ffmpeg

it may not appear to be installed since it is a program that is used through the terminal

to convert the videos cd to the dorectory then type

ffmpeg -i file name -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4

and change the file name to the name of the file you want to convert including the extension then the out put should be the video named M4V00002.MP4 in that directory

so navigate to the folder of the video

for example with a video called video with an mpeg extension you would call it video.mpg

cd ~/videos   (then press enter)

ffmpeg -i video.mpg -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4

your video name might be differant

---

### Post by NULL712 on 2007-08-23
ok i did every thing you said and the movie works on my computer but not on my psp. when i try to play the movie on mt psp it just gives me an error saying the video can not be played....any ideas?:confused:

---

