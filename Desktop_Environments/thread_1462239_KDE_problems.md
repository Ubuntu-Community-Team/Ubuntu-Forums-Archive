---
title: "KDE problems"
date: 2010-04-25
forum: Desktop Environments
---

### Post by Terryracoon on 2010-04-25
Help! KDE won't work! From what i could get it's a problem with plasma! When i log in plasma asks for a password (and i type it) but then it gives me a blank screen instead of my desktop! (some of the keyboard shortcuts work however such as Alt+F2 to type in a command) but the desktop (and the panel) won't show

---

### Post by shaka_zulu on 2010-04-25
What did you do before that? Some update? Video driver installation? Forced shut down?

---

### Post by Terryracoon on 2010-04-25
> **shaka_zulu said:**
> What did you do before that? Some update? Video driver installation? Forced shut down?
Nothing! Just normally used (okay, i installed a couple new themes and widgets, does that make any difference?)

---

### Post by shaka_zulu on 2010-04-25
Actually yes! I had problem with new themes few times. Try to go to system settings and change theme to default one. Restart X and it should work.

---

### Post by Zorael on 2010-04-25
First I'd check packages. Hit Alt+F2, run Konsole.
```
$ sudo aptitude update
$ sudo aptitude full-upgrade
```
Then, try to restart plasma and see if it spouts any errors.
```
$ kquitapp plasma-desktop
$ plasma-desktop
```
If it complains that there is no plasma-desktop command, you're missing plasma.
```
$ sudo aptitude install plasma-desktop
```

---

