---
title: "Recovering invisible processes"
date: 2008-05-08
forum: Desktop Environments
---

### Post by DarkerStar on 2008-05-08
i have had a problem with crashing programs that don't... "die" completely, but rather seem to be running perfectly well, just without any GUI any more. They're still logging and doing their thing... i just can't control them anymore. i can see these programs in the System Monitor, and if i really want to, i can kill them. But i was wondering if it was possible to *not* kill them, and instead force them to recreate their GUI in some way.

In particular, Wine does this a lot. Can these programs be resurrected by forcing them to redraw or something? And if so, how?

---

### Post by garyedwardjohnston on 2008-05-08
I doubt it.

Make sure to check winehq for compatibility issues.

---

### Post by DarkerStar on 2008-05-08
i don't imagine this is a wine-specific problem. The application has a platinum compatibility rating, and this kind of crash isn't unique to wine apps. Firefox used to do it (the one right out of the Ubuntu repository, not run through wine), but doesn't any more.

i figure that applications do get redraw notices when you do things like change the window decoration set (or other such settings). If the application is still running, then it is probably not an application crash at all, but rather a crash of some sort in the windowing system.

---

