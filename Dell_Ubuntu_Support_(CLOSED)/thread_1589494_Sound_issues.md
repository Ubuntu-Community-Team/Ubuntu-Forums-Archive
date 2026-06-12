---
title: "Sound issues"
date: 2010-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Merthod on 2010-10-06
Here I expose one issue and a couple of questions (Inspiron 9400/E1705 | Ubuntu 10.04.1):

The issue: how can I configure the volume media-keys to control application volume rather than general output volume? Or is there a key combination to do so? Or is there a remedy for the note below?

A note: the keys control the general output but it works strangely because below 20% I don't hear a thing; over 20% I hear my main speakers at full volume and as I raise the volume higher it is just the sub-woofer that goes up accordingly.

The question: what's the difference between "analog stereo output" and "analog stereo duplex" in the configuration of PulseAudio/ALSA Mixer? And why can't I use other configurations such as "digital stereo duplex" (if I choose it I don't hear a thing)?

Thanks

---

### Post by bobmartens on 2010-10-10
As far as I know, the multimediakeys only affect the master-volume, so not the volume of the application e.g. Movieplayer. It might be done by writing some code yourself, I guess...
The problems with the 'threshold' if I may call it so seem more likely to be caused by you external audio set. Is it jack-connected or USB? Do you have  the same issue with the built-in speakers? 
The pulseaudio/alsa mixer gives you some output options... choosing digital means that ubuntu will send audio to the 'digital out' of your system. If you don't have digital out, or nothing is connected to it: no sound! The same with analog... You can't send audio to a digital out and analog out at the same time. 
Duplex is a mode that allows simutaneous in- and output for a soundcard. Some former-century era devices did actually have problems with that. When using only one audio device, duplex makes no difference. Multiple devices however DO mind. 
Just do some testing: if you have the 20%-thing with the built in speakers also, it sounds like laptop hardware-issue. I might be wrong. But if they do the trick in their modest way, your speakers are the ones to look at. Set their volume-knob full-zero. Then, after selecting 'analog duplex' and your device as output, set all levels fully open.
Now gently up the volume on your speakers until things get ugly. Now try the controls on your laptop. They should provide gradual volume control.

---

### Post by Merthod on 2010-10-10
As of Ubuntu 9.04 I was able to configure which volume module I wanted to configure with the media key. Ubuntu 10.04 has changed it and now I can't find it the graphic way. Thanks for your interest.

---

### Post by bobmartens on 2010-10-19
Was my answer comprehensible/useful? 'd just like to know. my interest is free.

---

