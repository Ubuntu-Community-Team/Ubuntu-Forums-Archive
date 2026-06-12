---
title: "Package Manager Running Notification"
date: 2009-04-28
forum: General Help
---

### Post by kehon on 2009-04-28
this icon was really handy for me because i installed stuff via command line apt-get install and by using add/remove but now its not there so i dont know when one has ended cause i'm on another desktop its not that important but i would like that notification icon back because its not there

---

### Post by Brandon Williams on 2009-04-28
The answer for this is the same as for re-enabling the update-notifier status tray icon in general:
```
gconftool-2 --set /apps/update-notifier/auto_launch --type bool false
```

---

