---
title: "Openbox with two monitors, desktop icons only on one"
date: 2008-12-07
forum: Desktop Environments
---

### Post by Super Jamie on 2008-12-07
Hi all,

I installed Intrepid over the weekend, and set it up the same as I had my Hardy - with Openbox as a window manager, but still using Nautilus to draw the desktop, and with gnome-panel (this is selectable by using "Openbox\GNOME" session in GDM).

I have two screens on the one videocard, and am using nVidia TwinView to join them into one desktop, but with behaviour so I can maximise a window on one monitor only, and have two panels with a tasklist for each monitor.

However, under Intrepid with this setup, **I can only put Nautilus icons on one screen!** If I right click on the other screen, the Nautilus menu appears, xprop tells me it's a *WM_CLASS(STRING) = "desktop_window", "Nautilus"*, I just can't drag icons onto it.

If I switch to Metacity, everything works as expected, so I can't see that it's a problem with GNOME or Nautilus or even the nVidia driver.

I've logged an Openbox bug here, [https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/305670](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/305670) but is anyone else able to confirm this behaviour, or offer a fix?

Thanks,
Jamie

---

