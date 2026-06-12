---
title: "Latest Chrome browser dev not launching"
date: 2012-03-27
forum: Desktop Environments
---

### Post by thetick1 on 2012-03-27
I was using the Chrome Browser dev channel for years now and had no issues with google-chrome-unstable_19.0.1061.1-r125213_i386

With the latest Chrome google-chrome-unstable_19.0.1077.3-r128359_i386 it just hangs with ps showing [chrome-sandbox] <defunct>

I removed my ~/.config/google-chrome and ~/.cache/google-chrome directories thinking preferences were not backward compatable.  This happened before , but in this case it made no difference.  I was able to revert to google-chrome-unstable_19.0.1061.1-r125213_i386 and it worked fine then again I removed it and tried the latest withe same hang at launch.

Any ideas to debug before opening a Chrome Browser issue with Google?

I'm using [10.04 LTS]("http://en.wikipedia.org/wiki/Ubuntu_10.04_Lucid_Lynx") Lucid Lynx with various PPA updates.

---

### Post by thetick1 on 2012-04-06
Gee thanks for all the responses :(

19.0.1084.15 works fine.  I suspect the Google Chrome issue was fixed with "Fix sync issue with sessions (open tabs) triggering an unrecoverable error."

---

