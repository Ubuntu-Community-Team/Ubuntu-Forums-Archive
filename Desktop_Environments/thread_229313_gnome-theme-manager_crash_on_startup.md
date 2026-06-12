---
title: "gnome-theme-manager crash on startup"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Ger Teunis on 2006-08-04
I've installed the Dapper Drake 6.06 ADMD64 on my Shuttle ST20g5.
Everything works correctly but for some reason my gnome-theme-manager
wants to open a theme on a very weird location.

When I do an strace on gnome-theme-manager I see it is openening most of the themes okay, but at a point it will try to open the theme with location:

```
Window manager warning: Failed to read theme from file /usr/share/themes/&#65533;a\/metacity-1/metacity-theme-1.xml: Failed to o pen file '/usr/share/themes/&#65533;a\/metacity-1/metacity-theme-1.xml': No such file or directory
```

(With those weird character between themes and metacity-1.

I'm using ReiserFS on a AMD64 Dapper Drake,
Anyone able to help me out?

---

