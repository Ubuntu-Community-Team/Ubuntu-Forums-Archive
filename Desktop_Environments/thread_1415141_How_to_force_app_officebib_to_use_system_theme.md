---
title: "How to force app officebib to use system theme?"
date: 2010-02-24
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-24
Hi,
i have one duden programm officebib, but it doesn´t use system theme (similar as openoffice). I tried this line:
```
officebib_FORCE_DESKTOP=gnome officebib
```

as i fixed the openoffice:
[http://ubuntuforums.org/showthread.php?t=1065550](http://ubuntuforums.org/showthread.php?t=1065550)

I also made startup launcher:
```
Name: officebib
Command: export officebib_FORCE_DESKTOP=gnome
Description: Sets the officebib theme to the gnome theme
```

but, of course - nothing.

Found that officebib is using Qt theme ([http://wiki.ubuntuusers.de/OpenOffice.org/Duden_Korrektor#Office-Bibliothek](http://wiki.ubuntuusers.de/OpenOffice.org/Duden_Korrektor#Office-Bibliothek)) -not looking nice under ubuntu. But don´t know what to do next.

Any idea?

---

### Post by vickoxy on 2010-02-25
Well, i did some research-obviously there are some app having kde-qt theme. I have skype, vlc and officebib using qt style. I installed qt4 packages so i can set some stuff there, but still-if i choose in qt4 preferences gtk+ style, i have no significant changes.

Anybody knows if there is a way to set these themes properly in xubuntu?

---

### Post by vickoxy on 2010-02-26
Bump

---

### Post by vickoxy on 2010-02-27
Bump:
so to reformulate my question:

how to use system theme theme in xubuntu with qt programs?

---

