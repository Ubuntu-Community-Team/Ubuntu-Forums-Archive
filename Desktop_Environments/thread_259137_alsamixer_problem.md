---
title: "alsamixer problem"
date: 2006-09-16
forum: Desktop Environments
---

### Post by sixblades2000 on 2006-09-16
I started with two problems:  sound in windows XP was louder than ubuntu per same speaker volume settings and sound in ubuntu only plays from the right speaker.

Searching around, I found alsamixer and increased the output volume so sound is as loud as in windows.  However, im not sure how to tweak alsamixer to unmute the left speaker.

I have attached screenshots of my alsamixer options.  I'm not sure what any of the bottom selectables mean.  What do I need to change to unmute the left speaker?

The video card im using is a M-audio revolution 5.1 channel PCI card

---

### Post by mitch.c on 2006-09-17
alsamixer is cryptic at best. If it were me, I'd up DAC5 and unmute Multi TR (the one with MM under it); press M to unmute.

No guarantees just a slightly-educated guess.

Good luck.

PS. Turn on some music while you do this, your changes will be reflected during adjustment. Start moving sliders... it makes it easier to figure out which control makes a difference.

PPS. With my card, I found the gnome volume control exposes all these controls in a GUI which is much easier.

---

