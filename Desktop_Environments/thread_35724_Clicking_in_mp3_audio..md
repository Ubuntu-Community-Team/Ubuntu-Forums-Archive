---
title: "Clicking in mp3 audio."
date: 2005-05-20
forum: Desktop Environments
---

### Post by bdmp on 2005-05-20
I get clicking in mp3 audio. It makes it sound like a record and its really annoying.  Any suggestions?

---

### Post by philipacamaniac on 2005-05-20
Try increasing the playback buffer:

KDE Control Center --> Sound & Multimedia --> Sound System
and then slide the "Sound buffer" to the right. Just do it a little a bit at a time. A sound buffer all the way to the right would mean a pretty delayed output.

If that doesn't help, let us know what sound card you are using. Also, what are you playing the mp3 in? amaroK or Kaffeine (or something else...)?

---

### Post by bdmp on 2005-05-21
Moving the buffer to the right didn't do anything, but when I did a search to find out what my sound card was I found a faq for my same comp (averatec av 3225hs-20) and mandrake [http://www.kirstenray.com/averatec_linux/](http://www.kirstenray.com/averatec_linux/)

It said "Sound (VT8233 [AC97 Audio Controller])
Status After Install: Listed correctly under soundcard, with module "snd-via82xx" associated. However, I cannot hear any sound. All sound software works (no errors - i.e. mixer error), but I still hear no sound. I've checked the volume in the sofeware (i.e. CD Player, Mixer) and on the hardware.
How I Got It Working: Apparently two drivers matched my sound card and the default driver was the ALSA driver. All I did was change to an OSS drivers instead of the ALSA driver. This is done from the hardware configure menu."

That did it. Thanks for your help.

---

