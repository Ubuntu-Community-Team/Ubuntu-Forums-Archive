---
title: "915resolution no longer working"
date: 2007-08-23
forum: Dell  Ubuntu Support
---

### Post by emmajane on 2007-08-23
After applying the most recent set of upgrades (and then rebooting) my 915resolution patch for my external monitor is no longer working. I went back and checked the /etc/X11/xorg.conf file and nothing had changed there. When I went to System->Preferences->Screen Resolution there were two new resolutions listed where the correct ones used to be. I can't find a reference to these numbers in the config files though. I've tried:

/etc/X11/xorg.conf (under Modes)
/etc/default/915resolution

Where else should I be looking for this information? Help would be very much appreciated as the available resolutions make my (wide screen) external monitor virtually useless. Thanks!

---

### Post by emmajane on 2007-08-24
After doing a full power down and restart (instead of just rebooting), my screen resolution is working again!! Does this mean that the init.d loading information is not in the right section for a restart?

I still don't understand why it was temporarily wrong and why it is now right again, but I am very very happy to have my screen working the way it ought to. :)

---

