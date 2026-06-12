---
title: "Fluxbox notification area?"
date: 2007-05-01
forum: Desktop Environments
---

### Post by raul_ on 2007-05-01
I compiled fluxbox from source, like it's explained in a thread here in the forums. With that I had a fully functional notification area, but I don't know why, my fonts were all messed up.

Now I installed the version from the repos, and I don't have a notification area, which I need, because of the power-manager icon.

How can I enable it?

---

### Post by RedSquirrel on 2007-05-01
Do you mean the system tray?

```
grep toolbar.tools ~/.fluxbox/init
```

should give you:

```
session.screen0.toolbar.tools:  workspacename, prevworkspace, nextworkspace, iconbar, [COLOR=DarkRed]**systemtray**[/COLOR], prevwindow, nextwindow, clock
```

Does it?

---

