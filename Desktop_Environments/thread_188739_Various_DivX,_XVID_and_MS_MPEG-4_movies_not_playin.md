---
title: "Various DivX, XVID and MS MPEG-4 movies not playing"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Kray on 2006-06-04
Today I realized that quite a lot of my movies aren't playable in Dapper. In Breezy they were all ok if I installed gstreamer0.8-ffmpeg package. In Dapper I've installed similar package (gstreamer0.10-ffmpeg) and most DivX/VXID/MSMPEG4 files are ok, but many not. Interesting thing, that Nautilus create thumbnails for such files, but if I try to play them Totem hangs. 

Any thoughts? I was pretty sure that Gstreamer 0.10 will solve issues with a/v playback, but unfortenately it looks that it isn't so simple. Not that in Windows world codecs weren't messy thing too, but we are trying to be better, aren't we? ;-)

---

### Post by taurus on 2006-06-04
Did you remember to install w32codecs for Dapper too???

---

### Post by Kray on 2006-06-04
Nah, but those films are playable in Breezy just with gstreamer0.8-ffmpeg...

---

### Post by Xilon on 2006-06-04
I've got the same problem on amd64, excpet I can't install w32codecs... for obvious reasons

---

### Post by taurus on 2006-06-04
Try installing the Win32 codecs and see what happens!!!

---

