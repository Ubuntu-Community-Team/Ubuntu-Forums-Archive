---
title: "Sound only works for ONE program"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Flavian on 2006-08-29
Hy guys. I use the ALSA dirver on my laptop and I have encountered when I open a program that makes use of the sound card I am NOT able to run another program that makes use of the sound card as well. I always get a bug displayed.
For example XMMS tells me to check my sound card if I started Audacity before. That is very annoying, because I sometimes need another player to edit audio files.
Also with skype and XMMS it does the same.

Does anyone have any solution on that??
Thanks for your help
Flo

---

### Post by pampa on 2006-08-29
There are a few programs that still use OSS instead of ALSA by default. I think that XMMS is one of them and Skype is for sure another one. I'm not sure if you can change this on XMMS since I don't use it, but Skype is not easy.

A possible solution for Skype is in [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) under point 4.1 (that's what I found to work on my computer).

The new beta version of skype uses ALSA, but it doesn't seem to be stable enough yet.

Hope it helps

---

