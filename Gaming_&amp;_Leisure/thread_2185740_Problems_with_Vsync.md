---
title: "Problems with Vsync"
date: 2013-11-04
forum: Gaming &amp; Leisure
---

### Post by Rawit on 2013-11-04
I'm running Ubuntu 13.10, with the Nvidia 319 tested drivers on a GT 630. When running Steam games like L4D2, I get lots of tearing. So I tried to enable Vsync in game, but nothing seem to work. I also checked if Vsync was enabled in the Nvidia settings panel and tried toggling it, but I keep getting tearing.

The system runs on 1920x1080 on a TV through HDMI. No problems in other software, except it seems that the settings in the Nvidia panel are ignored. Does 13.10/Unity use xorg.conf?

---

### Post by DanglingPointer on 2013-11-05
1) Have you tried uninstalling your driver, then purging it?
2) If you ever had AMD drivers, try uninstalling that and purging it as well even though you are not using it.  Files could have been left behind causing conflict with Nvidia.
3) Reboot after 1 and 2 above
4) Reinstall the Nvidia propriety driver
5) Reboot and test (run Phoronix Unigine test suite)

---

### Post by Rawit on 2013-11-08
I replaced Ubuntu with eOS, but I could fix it there with "CLUTTER_PAINT=disable-clipped-redraws:disable-culling" added to /etc/environment. I'm not sure if this works for Unity though.

---

### Post by DanglingPointer on 2013-11-08
So you're done with Ubuntu?  Never heard of eOS, will check it out.

---

### Post by Rawit on 2013-11-08
Well not done, just experimenting with different distro's. I always return to Ubuntu, because it's still the most usable of the bunch. Elementary OS is based on Ubuntu with a Mac like interface. So far I like it.

---

