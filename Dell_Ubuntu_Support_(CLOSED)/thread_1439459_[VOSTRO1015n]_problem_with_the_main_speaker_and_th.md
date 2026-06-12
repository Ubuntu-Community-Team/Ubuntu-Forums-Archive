---
title: "[VOSTRO1015n] problem with the main speaker and the jack output"
date: 2010-03-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hgt1 on 2010-03-26
hi! im very new to ubuntu not sure if its the case on this issue. 

I updated the operating system all the way from 8.10 throught 9.04 to 9.10. 

Once i connect a headphone or a speaker to the jack output the main speaker of the laptop doesnt mutes. It did on the 8.10 version, couldnt get any sound working on 9.04 (didnt tried too hard tbh) and now from updating to 9.10 its working again but only this way. 

Tried to solve this issue by look after details in the gnome control center sound options and reinstalling the alsa driver from the given driver cd. these didnt helped.

Any thought how could i fix this, if its possible?

Thank you for your kind help.

---

### Post by zsitvaij on 2010-03-27
Installing linux-backports-modules-alsa-karmic-generic and rebooting should fix the issue, if you're on kernel 2.6.31-20 or newer.

---

