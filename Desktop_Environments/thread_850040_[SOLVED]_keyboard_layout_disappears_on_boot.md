---
title: "[SOLVED] keyboard layout disappears on boot"
date: 2008-07-05
forum: Desktop Environments
---

### Post by nikosm on 2008-07-05
Dear community,

I have three keyboard layouts that I use, configured to switch with left alt + shift. They work well, but every time I boot, alt + shift doesn't do anything. Clicking on the language indicator on the panel circulates between the first two layouts in the indication, but the layout doesn't actually change. Also, "show current layout" opens an empty window.

A fix I found is the following: open the keyboard preferences and add a fourth layout (e.g. Albanian) and remove it imediately. Alt+shift works and the keyboard layouts are there.

...but it would be nice not to have to do this at each boot! :)

Thanks a lot for any advice,
Nikos

P.S. It seems that adding a fourth language causes some service to restart - is it?

---

### Post by prshah on 2008-07-05
> **nikosm said:**
> 
I have three keyboard layouts that I use, configured to switch with left 
 add a fourth layout (e.g. Albanian) and remove it imediately. Alt+shift works and the keyboard layouts are there.

...but it would be nice not to have to do this at each boot! :)


Add the following command to your startup sessions```
setxkbmap
```; post back if you need more detailed steps. 

Eg, if you're using gnome, click on System-Preferences-Sessions-Add, then fill in the blanks as follows:

Name: setxkbmap (or whatever you like)
Command: setxkbmap 
Comment: Restore keyboard layout settings (or whatever you like)

---

### Post by nikosm on 2008-07-05
[QUOTE=prshah;5324374]Add the following command to your startup sessions```
setxkbmap
```

Thanks! That fixed it!

cheers,
Nikos

---

