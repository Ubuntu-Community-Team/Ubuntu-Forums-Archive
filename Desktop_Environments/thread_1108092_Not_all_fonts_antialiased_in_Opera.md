---
title: "Not all fonts antialiased in Opera"
date: 2009-03-27
forum: Desktop Environments
---

### Post by Kray on 2009-03-27
From time to time I run into pages where not all fonts are antialiased. Two recent example:
- [http://www.infoq.com/]("http://www.infoq.com/")
- [http://www.ubuntu.com/testing/jaunty/beta]("http://www.ubuntu.com/testing/jaunty/beta")
See attached screenshots (zoom a bit).

My guess is the for certain fonts and/or sizes aa is disabled. I've looked into /etc/fonts/conf.d/ folder, but could not find relevant rules. I'm not sure if it's Opera, KDE or Freetype thingie, either.

Firefox shows all fonts as antialiased.

Any advice?

Ubuntu 8.10 (one upgraded from 8.04 and one fresh, same behavior), Opera 9.64.

---

### Post by Kray on 2009-03-31
Damn... ;-)

No one is using Opera or am I only one experiencing this issue?

---

### Post by adamlau on 2009-03-31
Opera defaults to author mode CSS, use a modified CSS (user mode) to overcome this.

---

### Post by Kray on 2009-04-15
For those interested - uncheck 'EnableCoreXFonts' (opera:config#UserPrefs|EnableCoreXFonts) and restart the browser.

---

