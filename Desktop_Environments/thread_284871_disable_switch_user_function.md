---
title: "disable switch user function?"
date: 2006-10-26
forum: Desktop Environments
---

### Post by bmkrein on 2006-10-26
Hi 

In computer lab there is a need to disable "Swich User" button (or Swich User function) in log out window. Same time would be nice to disable "Hibernate" button (function). Need is to do it system-wide.

I looked Lockdown Editor pessulus, but options i see there are only connected with screen-saver function. 

Sincerely, 
Bmkrein

---

### Post by CatKiller on 2006-10-26
```
gconf-editor
```

/apps/gnome-screensaver/user_switch_enabled

---

