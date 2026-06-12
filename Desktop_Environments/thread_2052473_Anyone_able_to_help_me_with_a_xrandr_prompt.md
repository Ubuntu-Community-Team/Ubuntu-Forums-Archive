---
title: "Anyone able to help me with a xrandr prompt?"
date: 2012-09-03
forum: Desktop Environments
---

### Post by Macfunky on 2012-09-03
In Ubuntu i have no problems setting up my dual monitor set up using -

xrandr --output DVI-I-1 --left-of DVI-I-2

I then go into display and change the resolution of one of the monitors. Using LXDE i can't seem to change the resolution using the display settings tool. It simply won't apply the changed settings for some reason so i'm wondering, can i include the screen resolutions into the xrandr prompt? My left screen is 1280x1024 and the right one is 1440x900. Anyone able to help me to do that?

---

### Post by The Cog on 2012-09-03
Just a guess:
```
xrandr --output DVI-I-1 --left-of DVI-I-2 -s 1280x1024 --output DVI-I-2 -s 1440x900
```
It may be worth installing **arandr**, which is a graphical front-end to xrandr.

---

### Post by Macfunky on 2012-09-03
> **The Cog said:**
> Just a guess:
```
xrandr --output DVI-I-1 --left-of DVI-I-2 -s 1280x1024 --output DVI-I-2 -s 1440x900
```
It may be worth installing **arandr**, which is a graphical front-end to xrandr.

That's all the info i needed. Thank you very much :) Didn't know about arandr :)

---

