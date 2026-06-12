---
title: "completely disable Super_L keybinding to menu"
date: 2012-01-01
forum: Desktop Environments
---

### Post by arguson on 2012-01-01
There are no references to Super_L keybinding in lubuntu-rc.xml file and editing /usr/share/lubuntu/openbox/rc.xml didn't do the trick either.
All my new keybindings work but I cannot eliminate Win key bringing up the lubuntu main menu.

---

### Post by Rodney9 on 2012-01-01
> **arguson said:**
> There are no references to Super_L keybinding in lubuntu-rc.xml file and editing /usr/share/lubuntu/openbox/rc.xml didn't do the trick either.
All my new keybindings work but I cannot eliminate Win key bringing up the lubuntu main menu.

Following this posting - 
[http://ubuntuforums.org/showthread.php?t=1422861](http://ubuntuforums.org/showthread.php?t=1422861)

and thanks to Domu - You can check the keyboard shortcuts already set up by looking at the output of:
```
grep -A 2 "<keybind" ~/.config/openbox/lubuntu-rc.xml
```

mine shows
> <keybind key="Super_L"><action name="Execute"><command>lxpanelctl menu</command></action></keybind><keybind key="Super_R"><action name="Execute"><command>lxpanelctl menu</command></action></keybind>



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by arguson on 2012-01-01
I've seen that posting but my lubuntu-rc.xml file doesn't have those entries... only entries for multimedia keys

---

