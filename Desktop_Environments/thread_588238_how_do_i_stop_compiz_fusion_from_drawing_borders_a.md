---
title: "how do i stop compiz fusion from drawing borders around panels"
date: 2007-10-23
forum: Desktop Environments
---

### Post by markp1989 on 2007-10-23
see the screenshot i posted , i have a background for the top panel, but the rest of the panel has that annoying border around it, its not there when desktop effects are off.

how can i keep desktop effects and get rid of the border around the panel?

---

### Post by praet on 2007-10-23
I would look for shadow settings, look in the "Window decorations" plugin and remove the panel class from the "shadow windows" textbox.  Something like "any & !(class=gnome-panel)" or "any & !(type=Dock)" might work.


If you are using emerald, then you can also modify the theme to use no border.

---

### Post by markp1989 on 2007-10-23
> **praet said:**
> I would look for shadow settings, look in the "Window decorations" plugin and remove the panel class from the "shadow windows" textbox.  Something like "any & !(class=gnome-panel)" or "any & !(type=Dock)" might work.


If you are using emerald, then you can also modify the theme to use no border.

i used this one "any & !(type=Dock)" worked perfectly thankyou

---

### Post by praet on 2007-10-23
Great.

---

