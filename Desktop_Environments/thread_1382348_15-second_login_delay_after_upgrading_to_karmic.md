---
title: "15-second login delay after upgrading to karmic"
date: 2010-01-15
forum: Desktop Environments
---

### Post by bcrowell on 2010-01-15
After upgrading to karmic, I noticed that it took an extra 15 seconds for it to finish logging me in after I entered my password. This was particularly noticeable to me because I use fluxbox as my window manager, and fluxbox normally starts up in less than one second on my hardware. It turns out that xsplash has a 15-second delay hardcoded into it before the brown splash screen goes away. If you're using Gnome, apparently Gnome has a mechanism to let xsplash know when it's done loading, so the brown xsplash screen will go away in less than 15 seconds. But if you're using a window manager other than Gnome that doesn't support this mechanism, the brown screen will stay there for the full 15 seconds, while you wait for it. Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/504403](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/504403)

If you're experiencing this problem, there's a very easy fix:

sudo mv /usr/bin/xsplash /usr/bin/xsplash_hidden

This just hides xsplash under a different name so that the login manager can't find it and run it. I found that it did not cause any problem to have xsplash unavailable. However, the reason I've suggested renaming it rather than deleting it is so that if it does cause a problem for *you*, you can just rename it back.

---

### Post by Rodney9 on 2010-01-15
Thank You

---

### Post by bcrowell on 2010-01-16
> **Rodney9 said:**
> Thank You

You're welcome :-)

If this is a bug that affects you, maybe you could go to [https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/504403](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/504403) and click on the thing that says it affects you.

---

### Post by hhh on 2010-01-16
This workaround WFM using standalone Openbox in Karmic. Thanks!

---

