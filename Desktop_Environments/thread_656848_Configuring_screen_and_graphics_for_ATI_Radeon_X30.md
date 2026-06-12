---
title: "Configuring screen and graphics for ATI Radeon X300SE"
date: 2008-01-03
forum: Desktop Environments
---

### Post by MeanStreak on 2008-01-03
Hi,

I have an ATI Radeon X300SE graphics card and a basic Plug'n'Play monitor. In Windows XP, my card and monitor supports 1024 by 768, however in Ubuntu I have no such luck. Using the GUI to set up screen size and graphics drivers does not seem to have any effect (it used to - forcing a test and then a reboot) - can anyone suggest how I can enable this on Ubuntu?

---

### Post by ~LoKe on 2008-01-03
Type this into a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
It'll be step by step asking you how you want it configured.  Or you could try and let it do it automatically by typing...
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart the xserver.

---

### Post by MeanStreak on 2008-01-03
The manual configuration looks complicated for a noob, despite the descriptions. I will go the auto route. How does one restart xserver?

---

### Post by MeanStreak on 2008-01-03
Okay - I think I answered my question by rebooting Ubuntu. Configuration settings worked - loving the new res. Thanks!

---

### Post by ~LoKe on 2008-01-03
> **MeanStreak said:**
> Okay - I think I answered my question by rebooting Ubuntu. Configuration settings worked - loving the new res. Thanks!

Sorry I didn't get back to you right away.  Glad it worked out!

---

### Post by ~LoKe on 2008-01-03
Oh, looks like I missed another.  You can restart x simply by pressing ctrl+alt+backspace.

---

