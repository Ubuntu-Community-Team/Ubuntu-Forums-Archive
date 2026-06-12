---
title: "Compiz disables itself"
date: 2010-11-01
forum: Desktop Environments
---

### Post by teeshep on 2010-11-01
Hey everyone,
I have a Dell Inspiron 1520 with nVidia 8600M graphics card.
I'm running 10.10 Maverick, and I've set up CompizConfig settings manager. Everything works just dandy, but it will sometimes disable all settings. Restarting X fixes everything, but I can't figure out why it disables in the first place. 
When disabled, all the visual effects are disabled (wiggly windows, transparency, desktop cube, etc.) The settings in System>Preferences>appearance>Visual Effects is set to Extra, and all my CompizConfig settings are the same. I haven't figured out any way to get it working again except by restarting X.

So far, the only times it has disabled like that are when I've set the computer to "suspend" or "hibernate", and a couple times when it has gone to screensaver while running on battery. It never does it while plugged in (but plugging it in will not restore the graphic effects)

I have no idea how to keep the graphic effects working. Perhaps it's related to me unplugging my computer and running on battery? If so, is there any way to turn off this setting?

Any suggestions would be greatly appreciated! Thanks,
-teeshep

---

### Post by teeshep on 2010-11-28
Sorry to bump, but I'd still like to know the answer to this! Thanks!

---

### Post by mipesom on 2011-02-06
Have a similar problem. But here disables itself immediately when I close Appearance settings. :confused:

---

### Post by Copper Bezel on 2011-02-06
Odd. I've only ever had it disable itself because I was throwing something at the graphics card it couldn't handle.

In any case, you don't need to restart X. Try the Fusion Icon or the DisPlex Appindicator, which will allow you to turn it on and off from the panel, or run compiz --replace from the Run Dialog (Alt+F2).

---

