---
title: "What makes a Firefox window change size during startup?"
date: 2009-01-23
forum: Desktop Environments
---

### Post by jis on 2009-01-23
[Bug report 228114]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/228114")  gives an impression Firefox window size may change during session startup. Firefox session is started as part of Xfce session. Title bar is drawn by different size information than the rest of the window. What might cause this inconsistency?

---

### Post by mali2297 on 2009-01-24
Is the window set to maximize?

---

### Post by jis on 2009-01-24
I use to use Firefox windows maximized.

---

### Post by mali2297 on 2009-01-24
> **jis said:**
> I use to use Firefox windows maximized.

Then try instead to adjust the window size manually. I think there is an inconsistency because both Firefox and the window manager wants to set the window size.

---

