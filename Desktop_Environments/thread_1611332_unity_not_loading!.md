---
title: "unity not loading!"
date: 2010-11-01
forum: Desktop Environments
---

### Post by Elie-M on 2010-11-01
i have the desktop edition which has gnome of course. I decided to try out unity. I installed it from synaptic, and relogged choosing netbook-edition. Unity didn't load (nothing on my desktop but the wallpaper and the mouse cursor)

If I want to see the unity desktop I must summon a terminal window and do:

export CLUTTER_VBLANK=none
mutter --replace


Why?? what does these commands mean and is there any fix for that?

---

### Post by Elie-M on 2010-11-03
bump

---

### Post by P4man on 2010-11-03
You have installed the complete ubuntu-netbook metapackage or only unity? If the latter, try the former .

---

### Post by kerry_s on 2010-11-03
just add "export CLUTTER_VBLANK=none" to your ~/.profile file. it's a simple work around for some problem vid cards.

**echo "export CLUTTER_VBLANK=none" >> ~/.profile**

you shouldn't have to do the "mutter --replace" after that.

---

