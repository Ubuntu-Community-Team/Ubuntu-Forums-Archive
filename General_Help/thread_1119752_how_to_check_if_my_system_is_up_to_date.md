---
title: "how to check if my system is up to date"
date: 2009-04-08
forum: General Help
---

### Post by trixman on 2009-04-08
just wondering  how can i check if my system is up to date by myself.

thanks:KS

---

### Post by Cheesemill on 2009-04-08
In a terminal type:
```
sudo aptitude update && sudo aptitude -y -s safe-upgrade
```

This will tell you which (if any) packages need updating.
To update your system type the above commands without the -s

Cheesemill

---

### Post by 3rdalbum on 2009-04-08
GUI method (and recommended method): System > Administration > Update Manager. Click "Check".

---

### Post by trixman on 2009-04-08
> **3rdalbum said:**
> GUI method (and recommended method): System > Administration > Update Manager. Click "Check".

thanks , a very nice feature and it looks for all the programs another plus over windows machines.


:KS

---

