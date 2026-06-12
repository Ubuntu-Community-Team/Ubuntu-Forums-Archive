---
title: "Can not login"
date: 2005-06-08
forum: Desktop Environments
---

### Post by remin on 2005-06-08
This morning I went to start up Ubuntu, and now it will not boot into the login screen, just hangs. I switched monitors, so Im guessing that may be the problem, I checked my x config to make sure that everything was set to [Generic Monitor], so I thought that switching monitors would be fine.
Any ideas?

---

### Post by Joeb on 2005-06-08
Did all you do was change the physical monitor?  If so, it should still work (assuming your new monitor can handle the refresh rates).  To test, though if it is the monitor, you could hook the old one back up and see if it works.  I would suspect it won't, though.

Now, if you changed monitors, is it possible that you also changed a video driver?  Maybe to the commercial driver?  A lot of times, if they have a problem they drop you out  to text mode.

If that's not the case, you might try posting your video card specs (ie nvidia model or ati model) and your x configuration file.

---

