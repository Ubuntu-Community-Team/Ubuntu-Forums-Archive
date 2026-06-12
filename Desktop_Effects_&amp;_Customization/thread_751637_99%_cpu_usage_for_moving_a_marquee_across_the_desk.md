---
title: "99% cpu usage for moving a marquee across the desktop!!!"
date: 2008-04-10
forum: Desktop Effects &amp; Customization
---

### Post by parkland on 2008-04-10
When i move a window around (wobbly enabled), uses 2%on cpu1, and 4% on cpu2.

When i make a marquee, desktop freezes, then choppy, looked in system monitor, only doese this when I make a marquee, ....

WTF???????

---

### Post by fracturedmorals on 2008-04-11
Open a terminal and type:
```
ps ax|grep compiz
```

If it returns multiple processes that look similar to this:
```
 3237 ?        SL     0:45 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --replace ccp
```
try killing one of them and seeing if that at all helps.

---

