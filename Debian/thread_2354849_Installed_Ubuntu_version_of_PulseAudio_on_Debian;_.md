---
title: "Installed Ubuntu version of PulseAudio on Debian; can't upgrade."
date: 2017-03-07
forum: Debian
---

### Post by MASTER260 on 2017-03-07
Hello.

So, a few years ago I wanted to use Skype on my Debian KDE system, but the sound wasn't working.  I found out it was because PulseAudio wasn't installed, and at the time PulseAudio wasn't yet available for Debian.  However, there was an Ubuntu version available, (just like Skype,) so, stupidly, I installed it.  Nowadays, I'm stuck on Debian 8 Jessie and if I want to upgrade to Stretch or Sid, it bteaks the system by removing a lot of essential packages.  I've tried tons of aptitude and apt-get combinations and so far nothing has fixed it.  I understand it's good to have a stable Jessie system, but I'm afraid that by the time the latest stuff from Stretch or Sid hits Jessie, they still won't work.  Trying to remove libpulse0 does the same thing as trying to upgrade, (i.e. breaks the system by removing vast parts of it,) and removing the PulseAudio dummy pqckage just makes the sound not work anymore.


Is there anything I can do?

Thanks,
M260.

---

### Post by howefield on 2017-03-07
Thread moved to the "*Debian*" forum.

---

### Post by arochester on 2017-03-07
How did you install it? Do you have Synaptic and if you do a search does it show? It must have been "more than a few years ago" because pulseaudio has been available since Squeeze(?)

---

