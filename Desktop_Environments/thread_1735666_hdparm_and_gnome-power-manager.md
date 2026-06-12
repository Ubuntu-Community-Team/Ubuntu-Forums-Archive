---
title: "hdparm and gnome-power-manager"
date: 2011-04-21
forum: Desktop Environments
---

### Post by CRAZyBUg on 2011-04-21
Hi,

I am running Ubuntu 10.10 Netbook Edition.
I noticed that some event (I think gnome-power-manager is triggering) is switching HDD's APM Mode from 254 to 128 when AC Power is removed, and around.

How can I configure that behavior?
I would like to use a APM mode which lets my HDD sleep on battery. Additional, I want that the HDD's APM stay on 128, when it's on AC.
I already looked at gconf but there seems to be no value to change this. Same goes for pm-utils. I am a little unsure which process is handling this event. And how to reconfigure it.

Cheers,
Sebastian

---

### Post by CRAZyBUg on 2011-04-22
Seems like there is no clean way to configure hdparm's battery/ac apm management.
I edited /lib/hdparm/hdparm-functions row 82 and 84.

By  searching for a reasonable way to modify hdparm's behavior, I  discovered that for my HDD it is not recommended using APM level 128  (Even if hdparm uses it as recommended setting). My HDD's  LOAD_CYCLE_COUNT increases nearly every 10 seconds, which is really  worse and wasn't yet noticed by me.
Using APM level 192 seems to be safe for me, starting with 192, the LOAD_CYCLE_COUNT stops increasing every few seconds.

While  I am using LAPTOP_MODE=600, DIRTY_WRITEBACK=600000 and  JOUNAL_COMMIT=600, I noticed that ´upowerd´, ´gnome-power-manager´ and  ´gconf2d´ are reading and writing from disk at least once every 2  minutes. Due to that, the HDD isn't able to sleep longer than  ~20seconds.

The problem I see here is, that if I kill  upowerd/gnome-power-manager I won't be able to use S2R, and when killing  gconf2d gnome config will be ****** up.
I will investigate how to fix that.

---

