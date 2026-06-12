---
title: "X cursor always appears in the center of my screen"
date: 2005-01-26
forum: Desktop Environments
---

### Post by gtdj on 2005-01-26
Everytime I start gnome, I always have X cursor on the center of screen and on top of every windows.(I have my other cursor moving - two cursor on the screen one in the center cannot moving, other one can)
I usually get rid of it by open Terminal Server Client and it disappears.

Why is it ? and how can I get rid of it ?
Once I start KDE it doesn't have X cursor screen like this.

---

### Post by gtdj on 2005-01-26
I found solution !

Add the line below to /etc/X11/XF86Config-4 in [COLOR=DarkRed]"Device Section"[/COLOR]

```
Option          "SWcursor"      "true"
```

and press ctrl + alt + backspace to Restart X

> 
[http://www.ubuntuforums.org/showthread.php?t=11689&highlight=cursor](http://www.ubuntuforums.org/showthread.php?t=11689&highlight=cursor)

---

