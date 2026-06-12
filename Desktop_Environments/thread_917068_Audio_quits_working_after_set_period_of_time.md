---
title: "Audio quits working after set period of time"
date: 2008-09-11
forum: Desktop Environments
---

### Post by PseudoOne on 2008-09-11
While running my desktop environment (KDE), I find that after a set period of time with no audio being outputted, I am not able to play any more sound (In amarok, I get the error "Xine was unable to initialize any audio drivers"), and no other application returns errors or messages.  I tried resetting Amarok's config, but this doesn't help Amarok, much less my system.  I can verify it must "time out" or similar after some time because if I restart my X-server it will start working again.  Does anyone know a solution to this?

---

### Post by Dave_Connor on 2008-09-11
Maybe pulse issues, try "killall pulseaudio" within terminal and then switch your sound preferences within "System > Settings > Sound" and switch it all to ALSA driver instead.

---

