---
title: "Can't use visual effects"
date: 2009-02-23
forum: General Help
---

### Post by alzorz on 2009-02-23
After i had used an external screen from my laptop(EEE 900) only using the help you could get from the screen resolution menu i can't use any visual effects anymore. I read that i should download "xserver-xgl" but can find that package. Anyone knows whats wrong and what i can do?

---

### Post by Thelasko on 2009-02-23
Restart xserver, this should detect your hardware again and fix your screen.

If this doesn't work run the command
```
xrandr -q
```
in the terminal and post the output.

---

