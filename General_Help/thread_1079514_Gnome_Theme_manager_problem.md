---
title: "Gnome Theme manager problem"
date: 2009-02-24
forum: General Help
---

### Post by neilzomg on 2009-02-24
IM having a gnome theme manager problem, heres what it looks like.

[[IMG]http://img12.imageshack.us/img12/8113/gnomeg.th.png[/IMG]](http://img12.imageshack.us/my.php?image=gnomeg.png)

---

### Post by mcduck on 2009-02-24
If you mean the warning about missing some GTK engine, without actually naming any GTK engine, you can safely ignore that.

It's a common practice to use empty engine definitions when creating themes. Current version of Gnome's Theme manager doesn't really understand that and as a result gives this warning. The theme, however, works correctly.

Of course if you get a similar warning that tells waht engine it's missing, that's for real and you should install the GTK engine the warning says it's missing.

In other words, when it's says *GTK+ engine " is not installled*, ignore the error. When it says *GTK+ engine "Aurora" is missing*, install the missing engine.

---

