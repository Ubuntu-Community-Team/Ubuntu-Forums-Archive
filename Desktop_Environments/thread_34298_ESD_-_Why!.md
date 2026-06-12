---
title: "ESD - Why?!?"
date: 2005-05-14
forum: Desktop Environments
---

### Post by JAW on 2005-05-14
I'm trying to figure out why ESD is the default sound system instead of the vastly superior ALSA. I'm having nothing but problems with my sound in Ubuntu all caused by ESD hogging the sound card. Could someone enlighten me as to why we are stuck with esd?

Thanks,
James

---

### Post by Knome_fan on 2005-05-14
ESD is not something you use instead of alsa, but something that runs on top of alsa. 

Its purpose is to let multiple application access the sound card at the same time, something alsa can't to out of the box if the soundcard doesn't do hardware mixing. (There is a way to let alsa do this without ESD, look around the forum if you are interested, but it's not without problems either afaik.)

And if you don't think you need multiple sounds, or ESD is just to much trouble, simply disable it under System - Preferences - Audio.

---

