---
title: "Kubuntu 9.04 Screen Garbage"
date: 2009-04-30
forum: Desktop Environments
---

### Post by GuiGuy on 2009-04-30
Not sure if this is "Desktop" or "Hardware", but I'll place it here for now;

Using Kubuntu 9.04 AMD64, nvidia 7300GT, 180.44 drivers

Intermittently the characters in applications and file managers on the desktop will turn to illegible garbage. Minimizing and restoring will usually restore legibility.

Is there a way to turn this feature off?  ;)

Seriously though, this bug has been debated for some time now so I'm surprised it hasn't been attended to.

Cheers

---

### Post by Zorael on 2009-04-30
To my knowledge it was tracked down to the way KDE4/Qt draws windows that say they don't have a background. A particular Fedora patch of old that brought better performance (to Compiz) introduced the issue, that somehow GNOME (and KDE3) worked around. It was decided the proper solution was to disable the patch downstream and live with the results.

Nvidia users (using the proprietary drivers) should be immune to this, though. They supposedly worked around the issue some time ago now.

See [the launchpad bug report](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254468). Tag yourself as "this affects me too" and maybe pipe in on how it affects Nvidiaers.

Googling turns up [http://www.kitterman.org/ScottK/2009/01/bug_254468_momentary_video_gar.html](http://www.kitterman.org/ScottK/2009/01/bug_254468_momentary_video_gar.html) with some history behind the patch.

---

### Post by GuiGuy on 2009-04-30
> **Zorael said:**
> 
See [the launchpad bug report](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254468). Tag yourself as "this affects me too" and maybe pipe in on how it affects Nvidiaers.

Googling turns up [http://www.kitterman.org/ScottK/2009/01/bug_254468_momentary_video_gar.html](http://www.kitterman.org/ScottK/2009/01/bug_254468_momentary_video_gar.html) with some history behind the patch.

Thanks. Appreciated.

---

