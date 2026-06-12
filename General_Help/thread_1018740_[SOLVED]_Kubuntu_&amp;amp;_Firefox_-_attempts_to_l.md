---
title: "[SOLVED] Kubuntu &amp;amp; Firefox - attempts to launch but fails."
date: 2008-12-22
forum: General Help
---

### Post by ww711 on 2008-12-22
I've currently got Kubuntu running as a virtual machine and upgraded my Firefox browser to 3.0.5. When I launch, it opens for a split second and displays 2 tabs and follows to automatically closes. However when I try again but close one of the tabs, it launches fine.

I've made a screenshot of the error.

Any ideas/thoughts on how to fix this?

---

### Post by cariboo on 2008-12-22
You may have a malformed url in Edit-->Preferences-->Home Page. Remove the url that is giving you problems, and restart Firefox.

Jim

---

### Post by ww711 on 2008-12-22
I can't seem to even get to the preference options, as soon as I try to access that part of Firefox's configurations, the application quits instantly.

I've also tried, uninstalling and reinstalling firefox from adept package manager.

Any other suggestions?

I've also tried safe mode too, still experiencing the same problem. I'm running KDE 3.5.

When running in safe mode via terminal, I get a 'bus error' as output.

---

### Post by ww711 on 2008-12-22
Managed to fix this by deleting my hidden .Mozilla folder, so I guess it must of been some settings somewhere that caused my Firefox to break.

---

