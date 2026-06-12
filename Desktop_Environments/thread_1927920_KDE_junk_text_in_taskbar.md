---
title: "KDE junk text in taskbar"
date: 2012-02-19
forum: Desktop Environments
---

### Post by jaanndd on 2012-02-19
I'm running ubuntu 11.10 with KDE, I don't know the KDE version but I just installed it today.

When adding the weather app to the taskbar, its "configure" screen left text on the task bar, on the left side. Logging out and rebooting multiple times doesn't clear it.

I tried deleting and reloading the weather app onto the task bar several times but that didn't work either.

It truly seems to be "zombie" text, ie the text from other running apps goes right over it.

Thanks in advance.

---

### Post by jaanndd on 2012-02-19
found the answer elsewhere on the internet:

** restore plasma to defaults **

kquitapp plasma-desktop
rm ~/.kde/share/config/plasma-desktop-appletsrc
plasma-desktop &

---

