---
title: "Problems with Gnome 3 after setting up dual monitors"
date: 2012-06-04
forum: Desktop Environments
---

### Post by ConsumingFire783 on 2012-06-04
I just got a new video card.  It's a PNY GeForce GT 520 card, installed in Ubuntu 12.04.  For inputs I've got an LCD monitor through DVI-D and an LCD TV through HDMI.  Prior to hooking up the TV, I was running Gnome 3 with no problems.  After hooking up the TV, each log-in defaults to basic Gnome.  Unity is having the same problem, and is defaulting to Unity-2d.  Any ideas on what's causing this?

---

### Post by viperdvman on 2012-06-05
I really don't see why GNOME 3 and Unity would revert to their fallback settings after installing a newer NVidia card. I've attached my netbook to an LCD HDTV and have not had this problem with my Unity in Ubuntu 12.04. But, I also run an AMD Radeon HD 4270 in my netbook with open-source driver... and the open-source AMD drivers run great in Linux compared to the NVidia ones.

Are you running the open-source "nouveau" driver or the proprietary NVidia driver? I only ask because my desktop did not like running Unity 3D or GNOME Shell with the "nouveau" drivers at all. It was either slow or reverted to fallback DE... and this is when I had my old lower-level 6-series NVidia paired with my mid-range 7-series.

If you are running the "nouveau" driver, then try installing the proprietary driver and reboot your computer. The proprietary driver also installs an app that helps you configure your NVidia, including setting up multiple monitors.

The current Ubuntu Guide ([link here]("http://ubuntuguide.org/wiki/Ubuntu_Precise")) also gives you information on installing proprietary drivers, configuring them, setting up multiple monitors, configuring xorg.conf if necessary, etc.

Hope this helps.

---

### Post by ConsumingFire783 on 2012-06-05
I'm using the proprietary Nvidia driver.  It's the most recent version of it available.  With the single monitor, it still runs fine, its only when I hook up the LCD tv that it reverts.

I'll browse through that link and see if there's anything useful in there.

---

