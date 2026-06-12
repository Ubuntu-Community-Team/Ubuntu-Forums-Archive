---
title: "Xubuntu 11.10 Shadow Settings"
date: 2011-11-04
forum: Desktop Environments
---

### Post by beppe_giorgi on 2011-11-04
Hi to all,
there is any way to change the intensity and/or the radium of the windows shadow in Xubuntu?
I have searched and found this:

[http://forum.xfce.org/viewtopic.php?id=2873](http://forum.xfce.org/viewtopic.php?id=2873)

but nothing is changed in my case (Xubuntu 11.10).

Thanks in advance to all.

---

### Post by gsmanners on 2011-11-04
That information there is outdated. The configuration you want is set by the theme, so you'd need to change the theme's rc. In my case, I did this:

```
cd /usr/share/themes/Albatross/xfwm4
sudo leafpad themerc
```

That will let you change the values. To test whether the values look correct, press alt+F2 and type

```
xfwm4 --replace
```

---

### Post by beppe_giorgi on 2011-11-05
Perfect!!!
There are docs to see what other options are available?
Ah... T H A N K   Y O U ! gsmanners =D>

---

