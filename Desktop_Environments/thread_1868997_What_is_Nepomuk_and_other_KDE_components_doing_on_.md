---
title: "What is Nepomuk and other KDE components doing on my GNOME??"
date: 2011-10-25
forum: Desktop Environments
---

### Post by lolpenguin on 2011-10-25
I have found some KDE components on my Gnome system, and I wonder how they got there and what they are doing there.
Examples are core excecutables, runtime data, core shared data, platform core library.
What should I do with them??

---

### Post by Erik1984 on 2011-10-25
You probably installed a KDE program. Programs have their dependencies and some depend on Nepomuk. So when installing such a program you automatically get some KDE packages. An example of an often used KDE app is K3B.

---

### Post by lolpenguin on 2011-10-26
The issue is, I have never installed a KDE application (to the best of my knowledge). It should be safe to remove these dependencies?

---

### Post by robert shearer on 2011-10-26
In a terminal run...
```
sudo apt-get autoremove
```

This will remove packages that no current apps depend on.
If your kde packages are not listed for removal then some app **may** be using them.

At the very least, if you remove anything, make a text file listing what you removed so when/if something subsequently errors you may know the packages to reinstall. :)

If you must err then err with caution and a plan B. :D

Cheers, Bob.

---

