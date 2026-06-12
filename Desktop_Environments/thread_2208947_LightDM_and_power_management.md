---
title: "LightDM and power management"
date: 2014-03-03
forum: Desktop Environments
---

### Post by balubeto on 2014-03-03
Hi

I installed Lubuntu 13.10 32-bit on a notebook and I have set the power management through the Power manager for Xfce.

Now, I realized that if I start the notebook and I leave it on the screen LightDM, my power settings are not applied. How come? Is there a way to configure the power settings on the screen also LightDM?

Thanks

Bye

---

### Post by ajgreeny on 2014-03-03
The xfce4 power-manager does not start until your lubuntu session starts and I do not think there is any way to get it running earlier, as it will also need many of the other utilities in xfce that also start with the session.

I do not know if there are any cli style power managers that are used, for example, by headless servers which could be started before your DE session, but that could be worth looking into.

---

