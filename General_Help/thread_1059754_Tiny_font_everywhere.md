---
title: "Tiny font everywhere"
date: 2009-02-04
forum: General Help
---

### Post by jyavenard on 2009-02-04
Hi

Not sure what I did ; but after a reboot all the fonts are tiny.

When I say tiny, I mean every text or icon is about 2-3 pixels high.

That's everywhere, from the login screen to once I've logged in and started my session.

Is there any way to reset this so it becomes readable again ?

Will have to be through the command line cause the GUI is unusable.

Thanks much in advance
Jean-Yves

---

### Post by jyavenard on 2009-02-04
Found a way to resolve it by adding in xorg.conf in the Screen section:
Option "DPI" "100 x 100"

---

