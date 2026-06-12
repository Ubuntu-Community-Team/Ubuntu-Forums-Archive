---
title: "Kubuntu Added to Ubuntu (Mouse Change Issue)"
date: 2009-12-16
forum: Desktop Environments
---

### Post by Froobloops on 2009-12-16
I added the Kubuntu desktop so I could try out KDE in my spare time.  However, in doing this it has changed it so that my mouse cursor is the KDE version in both Gnome and KDE sessions.  How do I get my default Gnome mouse cursor back?

---

### Post by Zerd on 2009-12-29
Did anyone figure this out? I have the same problem.

---

### Post by premamotion on 2009-12-30
Right click on the desktop -> Change desktop wallpaper -> Theme tab -> select the theme that`s currently used by you -> Personalization -> Pointer tab

That helps you?

---

### Post by Zorael on 2009-12-30
Also, you can change the X defaults.
```
$ sudo update-alternatives x-cursor-theme
```
KDE's default is oxy-white. Not sure what GNOME's is, but it's probably called human-somethingsomething.

---

