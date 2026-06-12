---
title: "qt4 applications in gtk environment"
date: 2010-05-30
forum: Desktop Environments
---

### Post by breek on 2010-05-30
the only qt application i use is vlc.
in ubuntu 9.10 vlc color scheme used to match my gtk theme (by default) but it doesn't happen now in 10.04.
any ideas?

---

### Post by tehweezil on 2010-06-12
Same problem here, and it's really driving me bananas because I happen to think that QT is hideous and when you end up with KDE apps mixing in with a mostly GNOME environment it only gets worse. So someone PLEASE help. Or I'm switching back from Xubuntu to Ubuntu

---

### Post by PGHammer on 2010-06-12
> **tehweezil said:**
> Same problem here, and it's really driving me bananas because I happen to think that QT is hideous and when you end up with KDE apps mixing in with a mostly GNOME environment it only gets worse. So someone PLEASE help. Or I'm switching back from Xubuntu to Ubuntu

The issue is largely that gtk and qt4 are almost mutually-exclusive, especially since they use different window decoration by default.  In that situation, it may make more sense to use a more neutral window manager (compiz is ideal for this) and window decorator (any window decorator normally used with compiz, such as metacity or emerald), as opposed to the default for either environment.

For the longest time, I had the similar-but-opposing problem (GNOME/gtk apps in a KDE environment), which is all the harder now that KDE 4.5 beta 2 (technically, KDE 4.4.85) is my default DE of choice.  (There are still several gtk/GNOME apps I prefer to their KDE equivalents, such as pidgin.)  Switching from Kwin (KDE's default window manager) to compiz (along with using metacity for window decoration) solves the issue rather neatly.

---

### Post by tehweezil on 2010-06-13
> **PGHammer said:**
> The issue is largely that gtk and qt4 are almost mutually-exclusive, especially since they use different window decoration by default.  In that situation, it may make more sense to use a more neutral window manager (compiz is ideal for this) and window decorator (any window decorator normally used with compiz, such as metacity or emerald), as opposed to the default for either environment.

For the longest time, I had the similar-but-opposing problem (GNOME/gtk apps in a KDE environment), which is all the harder now that KDE 4.5 beta 2 (technically, KDE 4.4.85) is my default DE of choice.  (There are still several gtk/GNOME apps I prefer to their KDE equivalents, such as pidgin.)  Switching from Kwin (KDE's default window manager) to compiz (along with using metacity for window decoration) solves the issue rather neatly.

Yea I know, I'm using Compiz and Emerald. My only problem is when some of my apps use QT themes, I'd really prefer the GTK theme that I selected in the settings manager and not the one that VLC has decided for me to use all of a sudden lmao

---

