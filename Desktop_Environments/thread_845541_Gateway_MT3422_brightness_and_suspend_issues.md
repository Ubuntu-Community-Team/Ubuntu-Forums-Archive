---
title: "Gateway MT3422 brightness and suspend issues"
date: 2008-06-30
forum: Desktop Environments
---

### Post by i_lukas_podolski on 2008-06-30
I am not sure if I am posting this thread in the correct section of the forum, but since my current problem is only with KDE and not GNOME, I think this might be a good place to ask.

I have a Gateway MT3422 laptop running Ubuntu 8.04 with GNOME and KDE4.1 beta2 installed. I have had issues earlier with the GNOME setup, where the brightness keys on the keyboard were never recognized, and once the laptop went into sleep more or standby, it would only return with a blank screen with the backlight turned on but no test on the screen.

I tried looking for a solution, but not finding any on the forum, I decided to change settings, so that the laptop never went to sleep or standby mode. With this change, the display would shut off after a period of time, but a trackpad motion or keyboard tap would wake it up again.

Is there a way to achieve a similar setting in KDE4.1 beta2 ? I have tried using System Settings to disable all the sleep/standby settings, but with no success. Any help is appreciated.

---

### Post by moonlitaura on 2008-08-30
My sound worked with no difficulty and I still don't have my brightness/volume keys working. But, to fix the suspend issue, I installed the EnvyNG package which downloads some bleeding-edge Nvidia drivers. After installing these drivers and rebooting, I no longer had the sleep/suspend issues.

---

