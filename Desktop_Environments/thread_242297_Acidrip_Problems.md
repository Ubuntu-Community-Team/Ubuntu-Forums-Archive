---
title: "Acidrip Problems"
date: 2006-08-23
forum: Desktop Environments
---

### Post by ahaslam on 2006-08-23
I installed acidrip from the repo's a while ago and just gave it a spin earlier today.

I ripped my DVD to xvid in under an hour which was very quick for my laptop.

The problem is the quality, it lacks detail & sound lags a sec. I'd set the file size to a very generous 1024MB so I was expecting a very detailed video.

Upon inspection, the output file was a mere 329MB & the sound quality was only a fraction of what I specified.

Has anyone else experienced this problem?

Tony.

PS. Here's what I entered in to the Terminal:
```
mencoder dvd://1 -dvd-device /dev/dvd  -aid 128   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts abr:br=160  -ovc xvid -xvidencopts bitrate=1272 -vf pp=de,crop=720:416:0:80,scale=542:-2    -o "/home/ahaslam/Desktop/16_blocks.avi"
```
And here's the details of the resulting file:
[ATTACH]14738[/ATTACH][ATTACH]14739[/ATTACH]

Cheers ;)

---

### Post by ahaslam on 2006-08-25
Just to make things stranger, KDE shows the file as a Microsoft video. I've not used M$ in over six months :-k 

[ATTACH]14806[/ATTACH]

---

