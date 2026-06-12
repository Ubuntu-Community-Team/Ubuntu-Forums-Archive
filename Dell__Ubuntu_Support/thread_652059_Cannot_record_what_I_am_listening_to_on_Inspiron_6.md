---
title: "Cannot record what I am listening to on Inspiron 6400"
date: 2007-12-28
forum: Dell  Ubuntu Support
---

### Post by johnw2007 on 2007-12-28
I have an Inspiron 6400 which came pre-loaded with Ubuntu 7.04. I have installed the Ubuntu upgrade to 7.10 and, after applying various patches, everything seems to be OK.

However, I am now trying to use Audacity to "record what I am listening to", instead of having to switch to VMWare and Windows to do it. As I understand it, there is supposed to be an option in the Audacity mixer toolbar dropdown menu for "Stereo Mix" or something similar, but I do not see that. There are only the options for recording from the microphone socket.

I have read that Dell provided Windows sound drivers that were inhibited from doing this, so I suspect it is an issue with the sound drivers, but has anyone with Ubuntu been able to get this working?

asoundconf list gives:
Intel

cat /proc/asound/card0/codec#* | grep Codec gives:
SigmaTel STAC9200

In Sound Preferences I am using:
HDA Intel (Alsa Mixer)

The Alsa modules are version 1.0.14-1ubuntu.

Audacity is version 1.3.3 Beta, although I suspect it is not an Audacity problem.

---

