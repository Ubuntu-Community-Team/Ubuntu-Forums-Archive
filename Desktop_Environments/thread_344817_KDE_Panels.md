---
title: "KDE Panels"
date: 2007-01-23
forum: Desktop Environments
---

### Post by tpg on 2007-01-23
I am trying to create a separate taskbar panel in KDE, in order to achieve a similar effect to the default Gnome arrangement. However, if I create a child panel, and then try to resize it smaller (by right-clicking and "Configure Panel"), it just changes the size of the main panel, leaving the child panel large. How do I get around this? Thanks in advance.

---

### Post by Jucato on 2007-01-23
This seems to be a bug starting KDE 3.5.5. You need to restart Kicker (the KDE Panel) in order to see the option to choose which panel to resize. To restart kicker, press Alt+F2, and type

```
dcop kicker kicker restart
```

---

### Post by ComplexNumber on 2007-01-23
> **tpg said:**
> I am trying to create a separate taskbar panel in KDE, in order to achieve a similar effect to the default Gnome arrangement. However, if I create a child panel, and then try to resize it smaller (by right-clicking and "Configure Panel"), it just changes the size of the main panel, leaving the child panel large. How do I get around this? Thanks in advance.
when i were using kde(version 3.5.5 in PCLinuxOS) recently, i managed to set it up exactly like gnome with the main panel at the top and a small panel at the bottom. 
the reason why you are having the problem that you are is because you probably forgot to select the correct panel in the kde control centre. when you are (for example) changing the size, don't forget to select which panel you want to apply the changes to. then click on 'apply'.

---

### Post by tpg on 2007-01-25
Thanks everyone, I've got it working now. Next time I guess I should read all the options on the page!!:D

---

### Post by Jucato on 2007-01-25
Well, it's a confirmed bug, so even if you tried looking for the option, it won't be there unless you restart Kicker. Anyway, glad it works now for you.

---

