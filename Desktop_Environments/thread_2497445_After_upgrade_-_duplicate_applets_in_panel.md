---
title: "After upgrade - duplicate applets in panel"
date: 2024-05-05
forum: Desktop Environments
---

### Post by arst06d on 2024-05-05
Just upgraded to the latest LTS and have duplicate Dropbox and Bluetooth applet icons in the notification panel.  Each one seems to operate - ie shows dropdown menu when clicked.

[ATTACH=CONFIG]293730[/ATTACH]

Looking for clues how to resolve this, please.

---

### Post by #&amp;thj^% on 2024-05-05
Xubuntu 24.04 here as well, I had seen double bluetooth applets when in Development, I have no Dropbox installs.

Moral of my reply, Xubuntu still has some minor bugs to it. And sometimes a reboot solves it. But a cold boot, will show them again.

Not what you wanted to hear but for now just keep updating your system, hopefully they will iron out these small but annoying bugs.

If you want to see if this helps use:
```
xfce4-panel -r 
```

It should start again, but if it does not use:
```
xfce4-panel & 
```

---

### Post by arst06d on 2024-05-05
No joy with those - but thanks.
Everything seems to be working OK, just a minor irritation.

---

### Post by him610 on 2024-05-05
I have seen Panel duplicates also. I click on each one separately to see if they both call the programs they represent then I delete one of them.

---

### Post by &amp;KyT$0P# on 2024-05-07
What do you have listed in Panel Preferences > Items?

---

