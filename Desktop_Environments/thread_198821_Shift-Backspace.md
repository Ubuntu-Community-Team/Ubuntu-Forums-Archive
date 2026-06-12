---
title: "Shift-Backspace"
date: 2006-06-17
forum: Desktop Environments
---

### Post by nickdr on 2006-06-17
I find myself hitting Shift-Backsapce alot, which consequently restarts Gnome.... so is there anyway to disable this???

Thanks

---

### Post by JoshHendo on 2006-06-17
To disable it, simply go into "System -> Prefs -> Sessions". A box will now appear. Click on the "Startup Programs" tab. In that window, click "add". Now, type in:
```
xmodmap /usr/share/xmodmap/xmodmap.u
```
And click OK. Next time you login, Shift - Backspace should be disabled.

---

### Post by leohart on 2006-06-21
[QUOTE=JoshHendo]To disable it, simply go into "System -> Prefs -> Sessions". A box will now appear. Click on the "Startup Programs" tab. In that window, click "add". Now, type in:
```
xmodmap /usr/share/xmodmap/xmodmap.u
```
And click OK. Next time you login, Shift - Backspace should be disabled.[/QUOTE]

Shouldn't that be xmodmap.us ? Still, that is not a satisfactory answer. (unless you don't use Compiz)

---

