---
title: "Login Loop Nvidia Drivers"
date: 2016-11-04
forum: Desktop Environments
---

### Post by scpatl4now on 2016-11-04
I have spent a couple of hours trying to get through this.  Today when I tried to open Steam it didnt work.  I rebooted and was stuck in a login loop.  I have purged the Nvidia drivers (ctrl alt f2 since I could not log in the normal way) and rebooted.  I am finally back to my desktop, but I am running the X.Org X server - Nouveau driver.
I have tried reinstalling the Nvidia driver via addition drivers and by command line  since this always takes me back into the login loop after they are installed...regardless of how.  I would be fine with this, but Steam requires the proprietary driver...so I'm stuck?

Any thoughts?

I've seen a ton of people with similar problems (but not exactly like mine), but no one seems to have any answers or is even acknowledging that there is a problem

---

### Post by mateojonsonguynn on 2016-11-05
Noveau doesn't work with Steam. You need proprietary drivers. 

I also have this issue, and I'm stuck with it because the newest proprietary drivers break my system.

There's a bug on launchpad right now at status critical but it's not resolved yet. There's been no activity for a while.

---

