---
title: "Can't login to Desktop (And workaround)"
date: 2008-10-31
forum: Desktop Environments
---

### Post by Drate on 2008-10-31
If you find you can get to the GDM but it won't finish logging you in (black screen, mouse moves), then goto a failsafe terminal session and do this:

sudo apt-get remove compiz compiz-core

That should fix ya (well, allow you to login to Gnome anyway).

There is a launchpad bug: 277373

---

