---
title: "Font problem, how to change font in use"
date: 2010-08-27
forum: Desktop Environments
---

### Post by icegun on 2010-08-27
[COLOR=black][FONT=Verdana]Hi, sorry if I am missing the obvious solution to this problem, but here is my problem. I recently added some new font files from a well know font website. I had set fonts many times so know that I installed the font correctly, but my problem cam from when I set a particular font and since them I can't run any of the graphical menus or even change the font in the 'appearance' program. I created a new account that used default font setting and all programs load and run fine so I know it just a compatibility issue with my font and the kernel or something like that. How can I change the font that is used using command line in terminal? Am I correct in thinking that I need to edit some sort of user config file in my home directory?[/FONT][/COLOR]

---

### Post by wojox on 2010-08-27
Try:

Ctrl+Alt+F1

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Ctrl+Alt+F7

---

