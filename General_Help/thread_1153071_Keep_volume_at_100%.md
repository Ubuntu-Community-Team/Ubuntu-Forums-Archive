---
title: "Keep volume at 100%?"
date: 2009-05-08
forum: General Help
---

### Post by balderson on 2009-05-08
Hi. For some reason, Ubuntu keeps changing the system volume from 100% to about 75%. Is there anyway to constantly keep it at 100%? I think it changes to 75% after every sleep? 

The computer is being used as a media center and when the computer is at 75% the TV is way too quiet. Please help!!

---

### Post by lovinglinux on 2009-05-08
Go to "System >> Preferences >> Startup Applications" (aka Session), then click "+ Add" and put this on the command field:

```
amixer -q set "Master" 100% unmute
```

Give it a name like "Startup Volume" and click "+ Add".

---

