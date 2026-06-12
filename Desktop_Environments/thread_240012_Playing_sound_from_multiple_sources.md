---
title: "Playing sound from multiple sources"
date: 2006-08-20
forum: Desktop Environments
---

### Post by qwew on 2006-08-20
For some reason, I can't play sound from multiple sources at thesame time on my Ubuntu install. Is there any way to change this?

---

### Post by klytu on 2006-08-20
> **qwew said:**
> For some reason, I can't play sound from multiple sources at thesame time on my Ubuntu install. Is there any way to change this?

I think you will need to install and configure ALSA and then configure all of you apps to use it. I have this pretty much working on my system, which uses an old ES1938 sound card. There are still some situations where there are problems, usually due to conflicts with ESD or another sound daemon trying to run at the same time ALSA does. But for the most part ALSA seems to allow more than one source to play sound at once, for me.

This thread may be of help: [http://ubuntuforums.org/showthread.php?p=1193540#poststop](http://ubuntuforums.org/showthread.php?p=1193540#poststop)

Also search the forums for how to configure ALSA, and do a search for your particular sound card.

Once you have ALSA up and running properly, this is an excellent resource for detailed information and fine tuning of ALSA:
[http://alsa.opensrc.org/](http://alsa.opensrc.org/)

Hope this helps.

---

### Post by Thirsteh on 2006-08-20
If you're wondering why you can't play from multiple sound sources at the same time, it's because Linux, or ALSA, uses hardware mixing by default (not software mixing like Windows). So, if you don't have a soundcard with a hardware mixer (pretty much all onboard cards), you'll either have to go invest in a soundcard that does (they're pretty cheap) or use ALSA's experimental software mixing that klytu suggested.

---

