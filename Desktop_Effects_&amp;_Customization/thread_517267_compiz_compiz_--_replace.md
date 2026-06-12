---
title: "compiz/ compiz -- replace"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by superbungalow on 2007-08-04
What's the difference between typing "compiz" in the terminal to start compiz, or typing "compiz -- replace"?

---

### Post by hyperair on 2007-08-04
Compiz alone only works when there is no window manager running. Under normal circumstances, even when starting a session, the Metacity window manager is running. Compiz will complain that another window manager is running, then fail and exit. By putting --replace, Compiz will force Metacity out of its seat and take over.

---

