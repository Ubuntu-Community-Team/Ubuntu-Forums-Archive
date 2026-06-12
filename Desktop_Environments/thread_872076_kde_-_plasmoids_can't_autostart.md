---
title: "kde - plasmoids can't autostart?"
date: 2008-07-27
forum: Desktop Environments
---

### Post by jimmy the saint on 2008-07-27
Edit: This is in KDE 4.1 RC1

Every time I restart, the plasmoids disappear.  The ones in the taskbar show up.... but only the ones I haven't touched.  I accidentally deleted the pager in the taskbar, and put it back, but now it disappears too!  I have looked through all the settings and done a few google searches, but I cannot figure out how to make these darn things persistant.  Any help is appreciated!

JTS

---

### Post by kuja on 2008-07-29
I've had trouble with getting things to be persistent across sessions too ... panels disappearing and the like, no fun.

After you get things the way you like, do this in a shell:
```
kquitapp plasma && sleep 2 && plasma
```

---

