---
title: "Problem with msttcorefonts not configuring"
date: 2005-08-03
forum: Desktop Environments
---

### Post by Aragorn992 on 2005-08-03
So I have these running (manually copied the fonts and installed the packages), yet because it hasn't downloaded the fonts from the web it always says:

E: msttcorefonts:  subprocess post-installation script returned error exit status 1

Whenever I install any package. How do I "tell" Ubuntu that it is configured and to stop telling me this crap?

---

### Post by TravisNewman on 2005-08-03
It might be easiest to just install msttcorefonts and let it download the fonts.

---

### Post by Aragorn992 on 2005-08-04
And if I don't have an internet connection?

---

### Post by andril on 2005-10-18
You cna get them off of the Ubuntu 5.04 Add-On CD and I believe this will resolve your error code:
dpkg --forget-old-unavail :KS

---

