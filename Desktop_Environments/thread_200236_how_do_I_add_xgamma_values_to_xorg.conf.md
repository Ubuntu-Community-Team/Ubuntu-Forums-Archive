---
title: "how do I add xgamma values to xorg.conf ?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by railz68 on 2006-06-19
To make a long story short, I believe I've somehow damaged my moniter playing around with "gamma" settings in Windows. (playing around with color charts for digital photography).

Anyhow, my moniter has Green channel locked (RGB). I can adjust Red & Blue, but not Green. Everything I view has a strong look of green now.

In linux, what looks good to me is - 
xgamma -ggamma 0.85
xgamma -rgamma 1.00
xgamma -bgamma 1.00


I added this to the Moniter section in the /etc/x11/xorg.conf  and it failed. How and where should I add it ?.
I open a cmd prompt, and this works fine. I'd like it to load as default.

Looking at the file again, I did forget the "quotes" for the value. But of the 4 values in the Moniter section, 2 have quotes, 2 do not.

I guess I'll try it again with the values in quotes, just it scares the sh!t outa ya when xorg fails.

---

