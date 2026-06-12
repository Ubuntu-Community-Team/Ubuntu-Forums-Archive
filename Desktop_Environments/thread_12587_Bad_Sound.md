---
title: "Bad Sound"
date: 2005-01-25
forum: Desktop Environments
---

### Post by Lifer on 2005-01-25
I installed ubuntu yesterday and I managed to get almost everything working the way I want it, except the sound which is distorted, almost like its being over-amplified, and some games like chromium B.S.U have no sound. I have tried to fix the distortion by muting different channels in the mixer, with no success, and the volume settings never get saved even if they did work. Any help would be appreciated.

---

### Post by shmonkey on 2005-01-25
Distortion is often caused if the PCM volume is too high, try lowering this.
As for the settings not being saved have you got alsa in your any of your run levels e.g /etc/rc.2 or /etc/rc2.d and /etc/rc1.d ?

After you set the levels try running - sudo alsactl store

---

### Post by Lifer on 2005-01-25
It's funny because the sound is perfect in SLAX when I boot the livecd, and my /etc/rc.2 was blank and the other 2 don't exist. Any hints as what to add to /etc/rc.2?

---

