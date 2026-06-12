---
title: "gutsy alsa problem - no mic; no sounds in mplayer, vlc"
date: 2007-10-28
forum: Dell  Ubuntu Support
---

### Post by {spitFire} on 2007-10-28
I'm running Gutsy on Dell Inspiron E1505, and I'm having problems with my onboard sound card. 

When I run Skype, it doesn't record from my mic! Further I notice that I can't get sound from any of the following applications - mplayer, vlc; but totem, amarok and kaffeine work great! 

I also notice that in the Gnome "Multimedia Systems Selector", I get sound output only for "ESD" and if I set it to ALSA, I get the error "Resource Busy or not available".

Please, help me resolve the issue.

---

### Post by pieisgood4589 on 2007-10-28
Did you install the drivers four your mic? That's what solved my problem. Also, you might need to install some multimedia codecs.

---

### Post by {spitFire} on 2007-10-28
what drivers? you mean alsa-drivers-1.0.15? I installed that configured with options "--with-card=hda-intel" and it still doesn't work!

---

