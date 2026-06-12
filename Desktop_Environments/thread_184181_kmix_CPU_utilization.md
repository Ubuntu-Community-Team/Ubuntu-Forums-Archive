---
title: "kmix CPU utilization"
date: 2006-05-29
forum: Desktop Environments
---

### Post by seatek on 2006-05-29
After the dapper upgrade, is anyone else noticing that kmix goes wild, hogging all the CPU?

On my system, it's a little strange. It kills with a signal 15 just fine. When you first start it, it works fine for a few minutes. Then it starts taking up all the CPU cycles, though not so much so that it bogs everything else down, though it is a higher priority than, say, the boinc client, so boinc gets few cycles.

The time delay before it starts sucking up the cycles happens regardless of whether KDE system sounds are generated or not during it's well-behaved period.

The system is using ALSA with an Audigy 4 sound card, and artsd is running using ALSA.

I did notice, however, that using the "KDE sound system" with Full Duplex enabled resulted in lots of popping, as if the processor couldn't keep up (though it was fine). Full Duplex worked just great prior to the dapper update.

I had custom built alsa modules for the Audigy 4 using the same version of ALSA for each, yet the popping problem only happens in dapper.

I have no idea whether the two might be related in the murky depths of the KDE internals.

---

### Post by seatek on 2006-05-30
Murky depths indeed. kmix started behaving after upgrading Amarok to the 1.4 version that's referenced and strangely available off the main Kubuntu website (yet not in the repositories).

---

### Post by CitizenKane on 2006-05-31
I would guess that something in dapper is improperly utilizing the driver for your audigy 4 and causing soem part of it to hit an infinite loop.  So unfortunately it could be a lot of things.  It may be worthwhile to check out launchpad and see if there is a bug filed.

---

