---
title: "NUT - Need to power off 2 minutes after power is lost"
date: 2009-11-05
forum: Desktop Environments
---

### Post by msboston01 on 2009-11-05
Hello Ubuntu community.

I just migrated to 9.10 and everything works great. I have a UPS connected to USB port of my station and I use NUT to manage the power. I even have KNUTClient giving me a nice status every 30 seconds.

Right now, the shutdown command is set to the default which is when the status of the battery goes to low, the station will shut down. As a reminder, in the life of a UPS, there are roughly 4 status:
= UPS is online 
= UPS is on battery
= UPS is overload
= UPS is low (critical)

I want to change that and don't want to wait for the battery power to be critical. I want to start powering off 2 minutes after the status goes from online to battery. I am assuming that if the power is off for that long, then it's going to be a long power failure.

Anyone is familiar with this set up?

---

