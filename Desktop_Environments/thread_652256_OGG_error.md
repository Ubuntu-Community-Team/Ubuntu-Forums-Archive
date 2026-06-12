---
title: "OGG error"
date: 2007-12-28
forum: Desktop Environments
---

### Post by dgafhox on 2007-12-28
I recently ran into this issue and could not find any threads related so here is the problem and how I solved it...

1. My Rhythm Music Player would freeze when attempting to play any .ogg files
2. After this freeze, I was unable to play any sounds anywhere until reboot
3. Also, I would receive errors when trying to view any website that used any sort of sound, it would freeze Firefox
4. When I would try to change sound settings under preferences/sound, the window would freeze when I tried to 'test' the default auto detect
5. On start up, start up sound would play twice right over each other (weird)

Cause- I dont know what it was but I noticed that I had all my sound preferences set to auto detect. Changed them all the ALSA and same problem...

Solution- Changed all to OSS and all worked!

Question--??
Is there a solution to this that I did not find that involves installing different drivers? 

I tried to do this but since I am newbie to Linux I was unable to accomplish anything. Anybody that could point me in the right direction to dive into this a bit deeper and fix the problem with the auto detect or ALSA drivers would be much appreciated.

---

