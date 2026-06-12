---
title: "what are lock files and links"
date: 2006-01-09
forum: General Help
---

### Post by Omnios on 2006-01-09
Over the last six or so months I have been finding files named lockk on my system. Mostly in gnome but just found one in  usr  share. The ones in gnome seemed to lock out fireefox  making it unusable till the lock link was removed. Does anyone know about lock files is it a component or a lame hack?

---

### Post by dcstar on 2006-01-09
[QUOTE=Omnios]Over the last six or so months I have been finding files named lockk on my system. Mostly in gnome but just found one in  usr  share. The ones in gnome seemed to lock out fireefox  making it unusable till the lock link was removed. Does anyone know about lock files is it a component or a lame hack?[/QUOTE]
"Lock files" are usually used as sentinels to indicate that a particular event occurred (like a program or process startup), and are used by software to indicate if the process was able to end in the anticipated manner (which usually results in the lock file being deleted).

If a program crashes, then the lock file may not be removed and this can trigger a different action when the particular program starts up the next time (which may try and repair any potential file damage etc.).

If these things are a problem, then they are probably just the obvious symptom of another issue that needs resolving.

---

