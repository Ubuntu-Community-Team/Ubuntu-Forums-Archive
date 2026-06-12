---
title: "gnome-screensaver unresponsive"
date: 2010-03-16
forum: Desktop Environments
---

### Post by MgFrobozz on 2010-03-16
This started happening 2 days ago after the update manager ran; unfortunately, I didn't capture what packages were changed.

My screensaver is set for a blank screen. When I leave my system I invoke 'Lock Screen'. If I'm gone <5 minutes, and I move the cursor when I return, it presents the unlock dialog and everything works well. If I'm gone overnight, it presents only the cursor; the cursor moves normally, but I can't cause the dialog to reappear. 

This morning, I tried for about 5 minutes to get a dialog, then ssh-d from another machine and checked 'top'. There was nothing running over 2% of cpu. I killed gnome-screensaver. Almost everything returned to normal, except 'sudo': when I run 'sudo top', it takes about 45 seconds to present the prompt for the password. Once it authenticates, it runs any command normally.

Any ideas? Is the screen-saver issue related to the authentication issue?

```

> dpkg --list | grep screensaver
ii  gnome-screensaver                              2.28.0-0ubuntu3.5                          GNOME screen saver and locker
> cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
> uname -a
Linux stevens 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux

```

---

