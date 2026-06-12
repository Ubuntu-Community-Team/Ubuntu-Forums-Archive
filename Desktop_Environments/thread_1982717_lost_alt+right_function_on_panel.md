---
title: "lost alt+right function on panel"
date: 2012-05-19
forum: Desktop Environments
---

### Post by ottosykora on 2012-05-19
on the 12.04 classic, I now suddenly after an update lost the function alt+right on the panel, which means I am not able to add or remove anythnig or change anything.

Any help?

---

### Post by kansasnoob on 2012-05-19
> **ottosykora said:**
> on the 12.04 classic, I now suddenly after an update lost the function alt+right on the panel, which means I am not able to add or remove anythnig or change anything.

Any help?

If you're running a standard Gnome classic session - which uses Compiz - you must now press both the Alt & Super keys at the same time while right-clicking on the panel/applet you wish to edit, move, or remove. (The Super key is typically the one with the Windows logo).

If you're running Gnome classic (no effects) - which uses Metacity - you need only hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets.

To see whether you're running Compiz or Metacity you first need to install "wmctrl":

```
sudo apt-get install wmctrl
```

And then run:

```
wmctrl -m | grep "Name" | cut -c7-
```

Hope that helps.

---

### Post by ottosykora on 2012-05-19
you are the hero of the day !


I just forget that I was testing the 'full' version of the classic and use the noeff normally.


classic for ever!

---

