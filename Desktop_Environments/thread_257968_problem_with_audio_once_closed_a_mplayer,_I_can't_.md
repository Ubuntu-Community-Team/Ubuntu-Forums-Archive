---
title: "problem with audio: once closed a mplayer, I can't hear firefox sounds."
date: 2006-09-15
forum: Desktop Environments
---

### Post by simone.brunozzi on 2006-09-15
Hi there,
when I open mplayer (or even another audio player) to listen music, and then I close it (or even if I keep it open), then i'm not able to listen to firefox sounds anymore, like youtube video sounds for example.
Why is that?
Any hints?

Thanks!

---

### Post by Ciego on 2006-09-15
For some reason, mine will only work if I close firefox and then run it again.  This only happens when I use one of the other media players while firefox is running. It is a pain sometimes, but if you have a session manager enabled for firefox, it should't be a big deal.

---

### Post by Fixxxer on 2006-09-15
This should work:
```
sudo apt-get install alsa-oss
``` Then edit the file firefoxrc ```
sudo gedit /etc/firefox/firefoxrc
``` change FIREFOX_DSP="none" to FIREFOX_DSP="aoss"

---

### Post by bbango on 2006-09-16
fixxxer, that worked great. I was having the same problems with no audio. awesome

---

