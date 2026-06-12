---
title: "sound ? for et"
date: 2007-06-25
forum: Gaming &amp; Leisure
---

### Post by reston5 on 2007-06-25
I just installed enemy territory in my home folder and for some reason the game runs fine but has no sound i know this is probably really obvious but is there like a copy command or something i need to do.

---

### Post by wana10 on 2007-06-25
open a terminal and run this command, i had the same problem and this fixed it.

```
killall esd; et; esd
```

if it works just make a quick script to do this and link the icon to the script instead of where it is pointing to

---

