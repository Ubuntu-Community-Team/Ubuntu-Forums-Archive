---
title: "XFCE4 Problem"
date: 2005-09-04
forum: Desktop Environments
---

### Post by SparkyDawg on 2005-09-04
XFCE4 was running fine yesterday, and I needed to go into GNOME to do something. Anyways, I left GNOME on for awhile and then I wanted to log back into XFCE4. I did this, everything was normal except for my desktop was the GNOME desktop, and i cant right click to pull up my menu? What should I do?

---

### Post by astoltz on 2005-09-04
```
killall nautilus
```You might have to restart the xfce desktop too:  ```
xfdesktop &
```
Next time you exit xfce, be sure the "save settings..." box is checked.

---

### Post by SparkyDawg on 2005-09-04
thanks a bunch

---

