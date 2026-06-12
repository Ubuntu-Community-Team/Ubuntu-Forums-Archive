---
title: "Accidently deleted top panel in 10.04"
date: 2010-09-07
forum: Desktop Environments
---

### Post by MikeinVA on 2010-09-07
For whatever reason, I somehow deleted my top panel and couldn't shut down. I built a new one and have put some apps on it but still could use 'Places' any idea how to recreate that? Can my original panel be restored? I am still very new to this.

---

### Post by billyrobshaw on 2010-09-07
If I understood you: **Places **is inside the app called **Menu Bar**.

---

### Post by howefield on 2010-09-07
> **MikeinVA said:**
> Can my original panel be restored? 

Run these three 3 terminal commands

```
gconftool-2 --shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

Although I like the little script here...

[http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

---

### Post by MikeinVA on 2010-09-09
Right on! You have made my day! Thank you for the help, problem solved!!!

---

### Post by cbconway on 2010-09-10
:D You made my day, too. I felt stupid and tried everything I could think of, finally coming here to ask for help (gulp). Thanks!!!

---

### Post by nattriplett on 2010-09-14
Once again the forum has saved me from myself, Thanks:D

---

