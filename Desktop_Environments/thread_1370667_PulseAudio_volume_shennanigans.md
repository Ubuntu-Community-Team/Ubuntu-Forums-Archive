---
title: "PulseAudio volume shennanigans"
date: 2010-01-02
forum: Desktop Environments
---

### Post by Gannin on 2010-01-02
I'm using Karmic.

I've noticed something strange with my PulseAudio.  If I use my system like normal, it generally remembers the PulseAudio volume settings.  However, if I kill the PulseAudio server (pulseaudio -k) whether or not I restart it again before I restart my computer (pulseaudio -D) when I restart my computer the PulseAudio volume level is set back to 0.

Furthermore, when I set the volume level to where it should be, which is 50% on my system, the actual volume is different than it was before.  A quick check of alsamixer shows the underlying alsa levels haven't changed, but for instance, before going through the above process Pulse said 50% volume equated to -18.06 db, now it says 50% volume is -18.21 db.

Is there any way to save and / or manually manipulate the exact volume levels for Pulse other than using the standard sliders?  Some file that can be edited somewhere?  Thanks.

---

### Post by sigurnjak on 2010-01-02
Try  this  . I Had to edit/comment  out:

mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1

Mines on line 378. Someone had it on 379 or somewhere close to it 

in /etc/init.d/alsa-utils

and rebooted, worked a treat  .

---

