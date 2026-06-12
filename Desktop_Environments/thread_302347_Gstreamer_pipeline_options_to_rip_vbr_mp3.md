---
title: "Gstreamer pipeline options to rip vbr mp3"
date: 2006-11-18
forum: Desktop Environments
---

### Post by sickrandir on 2006-11-18
Just started to rip mp3 with sound juicer on edgy using the following pipeline:```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=1 ! xingmux ! id3v2mux
```
The problem comes when I try to play the mp3s because all of their duration are completely wrong.
It seems that the option **xingmux** doesn't work.
I also tried to use **xingheader** instead but with the same poor results.
Even if I try without the **id3v2mux** part I get the odd durations.
Someone can help?

Thanx

---

### Post by m.musashi on 2006-11-23
If you are using sound juicer, I just added "lame" and nothing else to the pipeline and it worked fine. The how to I followed gave me garbage for audio but just using lame worked fine.

---

