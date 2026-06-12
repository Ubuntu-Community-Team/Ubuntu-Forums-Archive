---
title: "Sound only works through headphones"
date: 2010-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by madjackrogers on 2010-05-14
I just updated to Ubuntu 10.4 from 9.10, and my sound system is apparently not working on some way.  I can play sound through my headphones, but it won't play to the laptop's internal speakers.  This is on a dell latitude d830 laptop, no hardware changes.  Any way I can fix this?

---

### Post by madjackrogers on 2010-05-15
anybody?

---

### Post by ZazzyE on 2010-05-15
Sweet! I just went through some sound issues on my d830.

In synaptic Package manager (under 'Preferences') install alsamixer, and play with the options there.  You run the terminal and type alsamixer into it, and it comes up in the terminal window.

The terminal is much like the "command prompt" in windows.

If that doesn't change it, install the alsa backports.  Those'll be in Synaptic too, and be a string of words with dashes between.  ALSA backport, linux 2.6.32.... all the funny specs will be in there, but you only need to install them and reboot.

If that doesn't change anything, I suggest leaving ALSA installed (you still need it) then install Pulseaudio preferences - this might put a LOT of new things on your computer, so don't be alarmed, it's all for the best.  You'll need them to make your computer show off against windows machines in voicechat programs on the internet.  In pulseaudio preferences, I got to choose what sort of device I have for sound input and output.  Play with that.  When Synaptic is done updating my box and I finish some housework, I'll see about hopping on to help ya.

---

### Post by madjackrogers on 2010-05-15
Excellent!  All I had to do was go into alsamixer and increase the volume on my speakers.  thanks a bunch!

---

