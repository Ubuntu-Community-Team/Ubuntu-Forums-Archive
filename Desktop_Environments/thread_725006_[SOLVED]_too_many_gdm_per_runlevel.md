---
title: "[SOLVED] too many gdm per runlevel?"
date: 2008-03-15
forum: Desktop Environments
---

### Post by abalone on 2008-03-15
I use KDE and Fluxbox predominantly (Gnome doesn't work properly but that's for another thread) but my window manager is still GDM.

rc0.d: K01gdm, K50gdm
rc1.d: K01gdm, K50gdm
rc2.d: S50gdm
rc3.d: S50gdm, K60gdm
rc4.d: S30gdm, K60gdm
rc5.d: S50gdm, K60gdm
rc6.d: K01gdm, K60gdm

I don't really know the first thing about this stuff, but this doesn't look sane to me. Should it really be started **and** stopped in runlevels 3, 4, 5, or stopped twice in runlevels 0, 1, 6? 

It's not that it's not *working*, but can I safely clean that up a little and delete some of those? (Which ones?) 

Please ease my habitual confusion

---

### Post by abalone on 2008-03-16
...maybe somebody with a more default-y installation could tell me what it looks like on their system?

PS: I'm sure this should go into the Absolute Beginners category, but I was too newb to have discovered it.

---

### Post by banewman on 2008-03-16
> rc0.d: K01gdm, K50gdm
rc1.d: K01gdm, K50gdm
rc2.d: S50gdm
rc3.d: S50gdm, K60gdm
rc4.d: S30gdm, K60gdm
rc5.d: S50gdm, K60gdm
rc6.d: K01gdm, K60gdm
GDM is the login manager for gnome - kdm for kde etc
rc2.d is the default GUI runlevel for ubuntu so S50GDM gives you the login window for that
rc3-5 aren't generally accessed so that shouldn't be an issue
rc0 is the shutdown runlevel and rc6 is the reboot runlevel and I have K01GDM in both of those - but only once - killing GDM twice should do no harm except adding microseconds to the shutdown/reboot time.
:)

---

### Post by abalone on 2008-03-16
> **banewman said:**
> GDM is the login manager for gnome - kdm for kde etc
rc2.d is the default GUI runlevel for ubuntu so S50GDM gives you the login window for that
rc3-5 aren't generally accessed so that shouldn't be an issue
rc0 is the shutdown runlevel and rc6 is the reboot runlevel and I have K01GDM in both of those - but only once - killing GDM twice should do no harm except adding microseconds to the shutdown/reboot time.
:)

Well, I'll throw out the extraneous ones and see if something explodes. (I also had KDM **and** GDM starting (or rather attempting to start) in ...whatever runlevel it was, I forgot; of course only one of them could run but it still seemed weird

---

