---
title: "mp3 sound"
date: 2006-08-04
forum: Desktop Environments
---

### Post by one_stinky_bum on 2006-08-04
Could someone please explain to me why mp3's sound better in amaroK than in banshee? I'm on Ubuntu 6.06 LTS and I've installed all the gstreamer 0.8 and 0.10 packages and xine (for amaroK).

I just switched from Windows and I'm trying to get something as good as iTunes. Sadly enough, both amaroK and banshee don't sound as good as iTunes when one cranks the volume up to "disturbing the neighbours" level (sorry, no dB meter here).

Thanks fellows. Linux rocks.

---

### Post by Lord Illidan on 2006-08-04
Try typing alsamixer in a terminal.

Adjust the pcm and WAVE meters to something like 77%.
You can leave the master up to 100%.

---

### Post by one_stinky_bum on 2006-08-04
Wow. That really does make a difference. AmaroK still sounds better though. Maybe it is a gstreamer vs xine thing. I don't have a WAVE channel BTW, here are the channels I have: 
Master
Headphone
PCM
Line
CD
Mic
Mic Boost (+20dB)
Video 
Phone
IEC958
PC Speaker
AUX
Capture
Mix
Mix Mono
External Amplifier

Is the Wave channel known as something else in the list above? 

Thanks for the rapid response.

---

