---
title: "Deleting files"
date: 2006-09-15
forum: Desktop Environments
---

### Post by ishimaru_kaito on 2006-09-15
From my windows days (sorry!) - I used to be able to switch off the confirm delete files option in a settings file somewhere (long time since I actually used windows!) - can I do this in Ubuntu?  I deal with a lot of photographic images from my camera usually named DSC*****.jpg going up numerically in sequence.  I copy them to a standard folder, where I sort them.  I would like to reduce my click count by switching off the 'Are you sure you want to remove to the wastebasket?' option as it gets tiresome after a few hundred images... :-)

---

### Post by Ramses de Norre on 2006-09-15
```
gconf-editor /apps/nautilus/preferences
```
and uncheck the "confirm_trash" key. (you can do this also somewhere in nautilus' preferences dialog btw)

---

### Post by ishimaru_kaito on 2007-01-26
Sorry it's been a while - thanks for the info - it works a treat, much better now :D

---

### Post by meng on 2007-01-26
Well, problem's already resolved I see, but you can also go from Nautilus:
Edit > Prefs > Behavior > and uncheck the box for confirmation before delete.

---

