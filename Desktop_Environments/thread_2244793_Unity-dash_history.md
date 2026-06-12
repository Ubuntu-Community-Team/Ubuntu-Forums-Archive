---
title: "Unity-dash history"
date: 2014-09-18
forum: Desktop Environments
---

### Post by jimbusch on 2014-09-18
I'm trying to find the file associated with the Unity-dash history. I'm also wondering if its possible to check the history from the command line.

---

### Post by mc4man on 2014-09-18
If you actually mean the Dash (tap super button/top icon in launcher) then that's just a temp 'history' & may be just stored in memory.
If you mean the command history (alt+F2), then that's stored in ~/.config/dconf/user & available thru gsettings or dconf-editor
```
gsettings get com.canonical.Unity.Runner history
```

---

### Post by jimbusch on 2014-09-18
Thank you for answering. I was actually trying to monitor the search history of the different machines on my local network. I was trying to do this from my main pc where I would'nt have to physically access the other machines.

---

### Post by Frogs Hair on 2014-09-18
I'm not sure what would be used to open the document/package and any history is easily removed from the privacy application by those aware of it. This location comes up in my search more than once but don't know for sure if this is what you are after. /.local/share/zeitgeist/activity.sqlite

---

