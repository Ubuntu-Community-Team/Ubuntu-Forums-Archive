---
title: "Desktop Icons for auto mounted SATA Drives, how do I get rid of them ?"
date: 2007-05-27
forum: Desktop Environments
---

### Post by forth on 2007-05-27
Hi I have two SATA drives for storage only, in my computer, running Ubuntu Feisty Fawn, and I am trying to lock down the desktop for a particular user but the SATA drives when they mount they put icons on all the desktops of all the users of this PC, how do I stop it from creating the desktop icons (for a particular user if possible if not then globally) without unmounting the volumes? I presume its a setting somewhere, but hell if I know where to even start looking! 

Thanks for any help

---

### Post by gruvsyco on 2007-05-27
not sure if this is what you're looking for or not.

```
gconf-editor
```

apps > nautilus > desktop

uncheck volumes visible

---

### Post by forth on 2007-05-27
> **gruvsyco said:**
> not sure if this is what you're looking for or not.

```
gconf-editor
```

apps > nautilus > desktop

uncheck volumes visible


Oh yes sweet Lord you've done it!!!

Thanks a million! 

:KS:KS:KS:KS:KS

forth gave this answer 5 stars out of 5.

---

### Post by gruvsyco on 2007-05-28
Glad I could help! :D

---

