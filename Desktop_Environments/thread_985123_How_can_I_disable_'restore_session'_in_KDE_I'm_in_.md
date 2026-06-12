---
title: "How can I disable 'restore session' in KDE? I'm in an auto-crash loop."
date: 2008-11-17
forum: Desktop Environments
---

### Post by BetterSense on 2008-11-17
When I log into KDE it always restores all my programs. But last time, I logged out because something made my xserver freeze. Thus when I log back in, it automatically freezes again. I'm logged into gnome right now, but how can I disable auto-session-restore or delete the list of applications to restore, without wiping out all my settings by deleting .kde?

---

### Post by GameManK on 2008-11-18
I think deleting the files in ~/.kde/share/config/session/
should stop all the currently saved stuff from restoring

---

### Post by benerivo on 2008-11-18
I'd agree with GameMank, but if that doesn't work, then possibly use Ctrl+Alt+F1 to get to a terminal screen, then use```
killall programname
```This might keep those programs out of your next session.

Or even```
apt-get purge packagename
```if you think you know which program could be causing the crash.

---

