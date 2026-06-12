---
title: "Centre windows title font metacity"
date: 2009-06-14
forum: Desktop Environments
---

### Post by Sashin on 2009-06-14
Does anyone know how to get the windows title font to the centre with the Dust theme?

I don't want to use emerald for this.

The dust theme places the window title text to the right.

---

### Post by Sashin on 2009-06-14
Bump!

---

### Post by Sashin on 2009-06-15
bump

---

### Post by p1rat on 2011-07-03
Alt+F2 "gksu nautilus /usr/share/themes"
Open the "theme-name" folder
Open the "metacity-1" folder
edit metacity-theme-1.xml
 
In the <!-- Window Title --> section replace;

x="1" with 
x="((3 `max` (width-title_width)) / 2) + 1"

x="0" with
x="((3 `max` (width-title_width)) / 2)"

---

