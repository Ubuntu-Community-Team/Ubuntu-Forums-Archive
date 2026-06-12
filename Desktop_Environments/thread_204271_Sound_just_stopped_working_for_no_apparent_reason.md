---
title: "Sound just stopped working for no apparent reason"
date: 2006-06-26
forum: Desktop Environments
---

### Post by fischer98 on 2006-06-26
I have an Audigy 2 sound card, and it's worked fine since breezy. Upgraded to dapper, no problem. I was watching an file in mplayer last night, and I went to hit the space bar to pause and fat-fingered some other key combination (don't know what), and now sound does not work at all. Reboot, other media programs, logging in as different users, reinstall alsa, headphones vs. speakers, none of it works. The system still recoginizes the sound card, and I have the volume control next to the clock, but no sound. Any ideas?

---

### Post by Winblowz on 2006-06-26
Have you tryed configuring your sound mixer program (KMix for KDE, etc.)?

---

### Post by fischer98 on 2006-06-26
I tried every config I could find. As it turns out, this gave me a hint:

[http://ubuntuforums.org/showthread.php?t=201523&highlight=sound+stopped+working](http://ubuntuforums.org/showthread.php?t=201523&highlight=sound+stopped+working)

similar problem. Mplayer was some how controlling the sound for the entire system. I usually run Mplayer from the command line, so I don't see the volume controls. Ran the gui and noticed the volume was turned all the way off, so I turned it up and viola! How very bizarre.

---

