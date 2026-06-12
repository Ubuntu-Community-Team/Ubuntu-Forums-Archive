---
title: "automount stopped working"
date: 2007-08-03
forum: Desktop Environments
---

### Post by azelter on 2007-08-03
I am currently running Ubuntu 6.06 LTS and a few days ago automount stopped working. I use the gnome environment and all the boxes are checked under System -> Preferences -> Removable Drives and Media. I have checked that gnome-volume-manager is running and it is. Also, if I log in as another user on this computer automount does not work either. This goes for all removable media. USB sticks are detected logged in /var/log/messages and can be mounted by hand using the mount command. CDROMs/DVDs can also be mounted by hand, but nothing automounts any more.
I would be very grateful if anyone could offer ideas on what I could do to get this working again.
Thanks in advance,
Alex

---

### Post by wkulecz on 2007-08-03
I seem to recall having this issue with 6.06. I think I triggered it by power down (perhaps impoperly from a screensaver lockup) with a USB stick mounted.  I removed the memory stick before turning on the power and rebooting.

I recall fixing the issue by shutting down.  Plugging the memory stick back in the same USB port and rebooting.

HTH, but it was a weird glitch that seemed to resolve itself.

--wally.

Edit, for what its worth I recenty had the same issue with Windows 2000 system where a memory stick shows up in "Unplug or Eject Hardware" but is not usable.  Ejecting and plugging the stick into a different USB port (different pair) it mounts.  Other sticks still mount in the "bad" port, but this one stick never mounts now if I plug it in to that one pair (real annoying as it happens to be the one on the front of the case).

---

