---
title: "gnome activity menu problem"
date: 2023-06-08
forum: Desktop Environments
---

### Post by gravjack on 2023-06-08
I have two pages of activity icons on my gnome desktop.  Suddenly I am unable to access the first page.  When I click on the menu it jumps to the second page.  I can pull the first page up by holding the mouse button, but as soon as it is released, it jumps back to page two.  Unable to figure out a solution.  Help appreciated.

---

### Post by douglas.e.ryan on 2023-06-08
Well, assuming you've rebooted the machine, and all that and can default out GNOME in the terminal like so:

```
dconf reset -f /org/gnome/
```

---

