---
title: "Dell Latitude, Xubuntu 22.04, issues with mouse and keyboard after idle time"
date: 2024-11-27
forum: Desktop Environments
---

### Post by bjdodo on 2024-11-27
I have installed xubuntu 22.04 on this new laptop.

First I noticed that if I leave it idle for 10 minutes I cannot click with the touchpad and I cannot type. The mouse pointer on the other hand moves, and I set up XFCE to keep replacing the desktop background images and that keeps working.

I can push ctrl+alt+F4 to get to a different session (not sure how it is called). If the GUI session is in this semi-frozen mode then I can switch away to the console session with ctrl + alt +F4 but  ctrl+alt+f10 does not take me back to the GUI session. If I kill Xorg then after logging in all seems normal.

I suspected that it has something to do with power management so I installed caffeine and that seems to make the idle time longer, but after an hour it happened again.

I can reproduce this condition immediately by executing
xset -display :0.0 dpms force off
(to turn the monitor off)
Monitor stays on, but mouse click and keyboard entry does not work, is not handled by X (but alt+ctrl+F4 works).

How do I investigate this any further?

Thank you.

---

### Post by ActionParsnip on 2024-11-28
Do you have the latest BIOS?

---

### Post by bjdodo on 2024-12-02
Now I have upgraded the BIOS, thanks for the idea. Did not help unfortunately. 

One more thing to add that I forgot, I left windows on the laptop as well (dual boot) and under windows the screen turns off perfectly,

---

