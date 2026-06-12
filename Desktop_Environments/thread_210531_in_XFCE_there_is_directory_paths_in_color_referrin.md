---
title: "in XFCE there is directory paths in color referring to missing screensavers"
date: 2006-07-07
forum: Desktop Environments
---

### Post by TOPPEL on 2006-07-07
In XFCE once xscreensaver has started there is directory paths in color referring to missing screensavers.

just a note.  

would love a fix.

---

### Post by VirtuAlex on 2006-08-08
It's definetely seems to be an example of a minor bug. Screensavers which ain't installed shouldn't be checked in screensaver settings by default. Going to Applications > Settings > Settings Manager, clicking on screensaver button and unchecking all grayed out screensavers should fix the annoyance. Or other way around you can just install missing screensavers:```
sudo apt-get install xscreensaver-data-extra
sudo apt-get install xscreensaver-gl-extra
```

---

