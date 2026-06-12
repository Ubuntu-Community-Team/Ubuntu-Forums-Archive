---
title: "/usr/lib/firefox, /usr/lib/firefox-version, /usr/lib/firefox-addons: why 3?"
date: 2008-09-16
forum: Desktop Environments
---

### Post by EmptyCinema on 2008-09-16
Why is there /usr/lib/firefox, /usr/lib/firefox-VERSION, and /usr/lib/firefox-addons?  (And on x86-64, there's also a /usr/lib64 version of each of the above).  I ask because something keeps creating a symlink in /usr/lib64/firefox-addons/plugins to a non-existent npwrapper.libflashplayer.so, which breaks flash for me.  I know the -VERSION can be used for version-specific information, but why the -addons and the regular one?

---

