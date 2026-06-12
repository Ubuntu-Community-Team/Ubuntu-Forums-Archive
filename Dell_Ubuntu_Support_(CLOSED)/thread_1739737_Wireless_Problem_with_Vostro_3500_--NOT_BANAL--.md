---
title: "Wireless Problem with Vostro 3500 --NOT BANAL--"
date: 2011-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by the.rider1290 on 2011-04-26
Hi all folks,
I got a problem with my laptop, a DELL Vostro 3500 with the DELL wireless 365 card.
I already installed broadcom drivers, but the problem is that if I plug in the power chord everything is ok, when I unplug it, network speed go down to 1%, the connection remain up but significantly unusable.

I already fixed a problem with backlight (editing Xorg,conf).... if u can help me it will be really good!

Thanks,
Luca

---

### Post by durand on 2011-04-27
It sounds like a powersaving feature to me. Try this when your wifi goes down:
Open a terminal (Application > Accessories > Terminal)
Type ```
sudo iwconfig eth1 power off
```
It should hopefully improve...

---

