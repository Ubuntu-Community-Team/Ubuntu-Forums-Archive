---
title: "Switching off realplayer support in mplayer-plugin"
date: 2005-12-01
forum: Desktop Environments
---

### Post by snooo on 2005-12-01
See subject. How does one do this? I'd rather use the native player than the mplayer plugin..

Dave

---

### Post by yoyoned on 2005-12-01
It took me a while to figure this on out.  Remove the following files from you plugins directory.

mplayerplug-in-rm.so  
mplayerplug-in-rm.xpt

the default location for these files is /usr/lib/mozilla/plugins/

---

