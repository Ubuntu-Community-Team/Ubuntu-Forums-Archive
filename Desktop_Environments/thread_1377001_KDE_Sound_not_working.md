---
title: "KDE Sound not working?"
date: 2010-01-09
forum: Desktop Environments
---

### Post by bobmatino17 on 2010-01-09
well i reacently installed 9.10, the standard version, and then installed KDE to have with it. it works great, better than the older versions, except for in the sound department, which it does not have. It is telling me that the drivers arent working...

---

### Post by Zorael on 2010-01-10
If you install Ubuntu first then you also install the PulseAudio sound server, which isn't part of Kubuntu. One of its features is that it imposes its own volume management, to provide the user with only one output channel (volume slider) instead of the several sliders that sound drivers generally do (Master, PCM, Front, etc). Pulse likes to mute those and give its own single channel supremacy. When you suddenly don't start Pulse, you'll find that they remain muted, and you don't get sound.

So, pop up the sound mixer (KMix) and make sure volumes have sane values and aren't muted. Several may affect output multiplicatively, so raise them one by one until you get output. You can run the following command in a terminal to play some looping sound while doing this, so you'll immediately know when you reach audible levels.
```
$ speaker-test -twav -c2
```
Hit Ctrl+C to stop it.

---

### Post by bobmatino17 on 2010-01-10
thank you. although the sound was rather annoying....

---

### Post by Zorael on 2010-01-10
:3

I don't know, kinda catchy, don't you think?

"Front left, front right, front left, front right, front left, front right, front left, front right, front left, front right, front left, front right, front left, front right, front left, front right, ..."

---

### Post by jdionne on 2012-05-18
Thank you thank you thank you
I recently installed KDE because i wan't happy with gnome, but the sound wasn't working.  This helped!!!

But I might add: make sure all of the volume controls are added to the GUI the speaker slider wasn't there by default and that was the one muted for me, know it works great!!! I love KDE

---

