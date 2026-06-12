---
title: "hoary 64bit, Point2Play, and alsa?"
date: 2005-04-16
forum: Gaming &amp; Leisure
---

### Post by ron1n1 on 2005-04-16
I followed the guide to install Point2Play in a native 64bit environment and it works great except for sound.

Point2Play will only seem to work with OSS drivers and when playing WOW I periodically get nothing but white noise.

I tried a link to libasound in /usr/lib32, but the sound test fails with an error 'can't open slave device.'

Has anyone been able to use Alsa drivers with 64bit hoary and Point2Play?

---

### Post by FrankBob on 2005-04-16
I had the same problem. The solution was to compile and install the latest alsa driver. Sound for WoW then works through OSS. 

See: [http://ubuntuforums.org/showthread.php?t=25655](http://ubuntuforums.org/showthread.php?t=25655) 

Hope this fixes your problem

Frank

---

### Post by ron1n1 on 2005-04-16
I tried compiling the alsa drivers from source, but that didn't help.  I still get he white noise or 'screeching'.  I'm using the intel8x0 driver.

I'm still hoping to get alsa working.

---

