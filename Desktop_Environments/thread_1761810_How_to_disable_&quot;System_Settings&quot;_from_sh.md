---
title: "How to disable &quot;System Settings&quot; from shutdown button menu"
date: 2011-05-18
forum: Desktop Environments
---

### Post by mrandredparis on 2011-05-18
How do you disable the "System Settings" from the shutdown menu?

---

### Post by mc4man on 2011-05-18
You can remove it by deleting the link in 
/usr/share/indicators/session/applications

```
gksudo nautilus /usr/share/indicators/session/applications
```
Then log out/in

---

