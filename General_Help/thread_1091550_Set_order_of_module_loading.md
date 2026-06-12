---
title: "Set order of module loading"
date: 2009-03-09
forum: General Help
---

### Post by Dumdideldum on 2009-03-09
Hi,

how can I make sure that my Ubuntu 8.10 will load two kernel drivers in an exact order. I have 2 TV cards and it is absolutely necessary, that the driver for Card 1 (ivtv) gets loaded before the driver for Card 2 (bttv) - otherwise mythtv won't initialise the cards correctly.
It happens sometimes, that the driver for Card2 gets loaded before Card1, therefore Card2 is linked to /dev/vide0, whwere Card1 should be linked to.

So where can I set this module order ?

many thx in advacne

---

