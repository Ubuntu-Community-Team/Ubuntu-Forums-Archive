---
title: "Primary monitor on dual monitor config has black border around screen."
date: 2011-12-28
forum: Desktop Environments
---

### Post by meekamoo on 2011-12-28
Hey all

I recently upgraded my nvidia to an ATI card and have encountered a strange problem with my resolutions.

I have dual monitor 23" and 22". Both running at full native res.

The 23" has a roughly 1" black border around it even though it is set to the correct resolution.

I'm running 11.04 with original ubuntu fglrx drivers. Tried ATI catalyst and I got a black screen on xorg startup (another issue)

Xorg config file: [http://paste.ubuntu.com/786391/](http://paste.ubuntu.com/786391/)

Any ideas as to why its doing this?

---

### Post by mukk85 on 2012-01-23
Not sure if you're still having problems but you need to go to Catalyst Control Center (Administrative) and expand the Display Manager click on the monitor that is the problem and go to the adjustments tab.

Set Scaling options to 0%.

---

### Post by trisapeace on 2012-04-13
Thanks mukk85. That worked for me.

---

