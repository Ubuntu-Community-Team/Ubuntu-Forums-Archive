---
title: "Close, Maximize, Minimize buttons disappear"
date: 2009-06-05
forum: Desktop Environments
---

### Post by SC2Sick on 2009-06-05
Fresh install of UNR on an Acer Aspire One with classic desktop mode.

When I log in the whole bar across the top with the window title and close, maximize and minimize disappears.

I can resolve it by going into appearance settings and changing to Extra and then back to none, but this is a major inconvenience and I am getting ready to sell this laptop soon.

Should I just do a fresh install or is there something I am missing?

---

### Post by pauna on 2009-06-05
> **SC2Sick said:**
> Fresh install of UNR on an Acer Aspire One with classic desktop mode.

When I log in the whole bar across the top with the window title and close, maximize and minimize disappears.


Do you still have the gnome-panels visible, so just the window top bar is gone?

Ubuntu 9.04 netbook remix has a bug where you lose gnome-panel and the window manager when you switch to classic view. You just have to manually launch "gnome-panel" and "gnome-wm" to get them back and make sure they're saved into your session. If you already have the panel(s), you can try to launch gnome-wm to see whether it brings back your window top bar.

---

### Post by kiennd on 2009-06-19
It's caused by "Maximus Window Manager" daemon, let's disable it in "Autostart" or remove maximus package, and then restart gdm. I solved my problem by this way! Good luck!

Regards,
NDKien

---

### Post by omegahalo on 2009-07-02
removing maximus seems to have done the trick!

---

