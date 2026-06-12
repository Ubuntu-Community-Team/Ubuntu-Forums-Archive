---
title: "Compiz Effects Always Slow After 'Reload Window Manager'"
date: 2011-01-07
forum: Desktop Environments
---

### Post by alsamman on 2011-01-07
Anytime I click Reload Window Manager, everything reloads fine but stuff like wobbly window and minimize/close effects lag and aren't smooth anymore and it stays like that until I log out and log back in. Before I click it, everything works perfect and smooth but I am not sure why it suddenly goes all laggy after a reload.

---

### Post by Krytarik on 2011-01-08
Where do you find this option, and why do you use it?

---

### Post by alsamman on 2011-01-08
On the compiz desktop icon, and I use it because sometimes the window border doesn't load for some reason when I log in so I have no close/maximize/minimize buttons but when I click Reload Window Manager it fixes it but then the effects get all laggy.

---

### Post by Krytarik on 2011-01-08
Check if you get the same behaviour by reloading Compiz with this command via Alt+F2 or a terminal:
```
compiz --replace
```

---

### Post by alsamman on 2011-01-08
> **Krytarik said:**
> Check if you get the same behaviour by reloading Compiz with this command via Alt+F2 or a terminal:
```
compiz --replace
```

interesting. When i do compiz --replace i dont get the lag; only when i use the compiz desktop icon to reload compiz. I guess its some problem with the icon

---

### Post by Krytarik on 2011-01-08
> **alsamman said:**
> interesting. When i do compiz --replace i dont get the lag; only when i use the compiz desktop icon to reload compiz. I guess its some problem with the icon
Cool! :D

Then you may just create a launcher for the command and place it in a panel.

---

