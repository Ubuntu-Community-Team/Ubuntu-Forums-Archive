---
title: "How do disable libgweather?"
date: 2011-02-21
forum: Desktop Environments
---

### Post by Dopameen on 2011-02-21
Does anybody know how libgweather module can be disabled without disabling the whole Ubuntu GUI. Libgweather seems to be entrenched in Ubuntu while I don’t see any reason why this should be the case as I’ve never used it since I’ve started using Ubuntu (from Gutsy on) nor have I seen anybody use it. It appeared on my radar after I saw my computer making outbound internet connections while I never looked for a weather forcast. Amongst others, it connects to noaa.org .

From a security point of view, all applications that make unnessary or unrequested in- or outbound connections are potential vectors of intrusion so it’s only logic that it’s disabled.

If I remove the linked files from my /usr/lib/ folder the next time I boot, the clock on the bottom right isn’t available anymore.

I used a hex editor to invalidate the hyperlinks in /usr/lib/libgweather.1.6.8.so but there must be a cleaner way to do this?

---

