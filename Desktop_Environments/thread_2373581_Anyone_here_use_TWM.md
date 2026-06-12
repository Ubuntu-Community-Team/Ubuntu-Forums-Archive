---
title: "Anyone here use TWM?"
date: 2017-10-07
forum: Desktop Environments
---

### Post by lokithefly on 2017-10-07
Seems like no one knows about TWM. I need help with it on Ubuntu. Anyone?

---

### Post by deadflowr on 2017-10-07
What do you need help with, exactly?

---

### Post by lokithefly on 2017-10-08
starting xterm. When I used Arch Linux, I used TWM. Xterm was an option in the menu, but it is not there when I start TWM from the login manager on Ubuntu. I tried adding xterm or gnome-terminal to xinitrc, but I read that it is not read unless you start TWM with xinit (startx).

---

### Post by steeldriver on 2017-10-08
I haven't used TWM since some time in the 1990s...

Try placing the xterm command in ~/.xsession or ~/.xsessionrc instead of ~/.xinitrc

See for example [Difference between .xinitrc, .xsession and .xsessionrc](https://unix.stackexchange.com/a/281923/65304)

HTH

---

### Post by lokithefly on 2017-10-09
Thank you.  ~/.xsessionrc worked. The problem is it also works for regular Ubuntu when I login. Is there anyway to just have it work for TWM?

---

