---
title: "The black thing"
date: 2006-06-24
forum: Desktop Environments
---

### Post by bekok on 2006-06-24
There was some guide which explained how to remove the black, box-sort-of-thing, when you minimize a window.
Does anyone know where the guide is/how to remove it? I've tried to search, but searching for things as "black" doesn't come out very good :)

---

### Post by Kouya on 2006-06-24
[QUOTE=bekok] black, box-sort-of-thing, when you minimize a window.
[/QUOTE]

???? Erm I dun see a black box. U mean the borders when u minimise to the taskbar?

---

### Post by bekok on 2006-06-24
Yeah, borders is a better word :P hehe

---

### Post by Kouya on 2006-06-24
er i have no idea but see if these sites are relevant...

[http://www.compiz.net/viewtopic.php?id=721](http://www.compiz.net/viewtopic.php?id=721)

[https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz](https://wiki.ubuntu.com/CompositeManager/ConfiguringCompiz)

cheers

---

### Post by rumli on 2006-06-24
If you are talking about removing the minimization animation (the sequence of black rectangles drawn when you click the minimize button), [this post]("http://ubuntuforums.org/showpost.php?p=195540&postcount=5") might help.

From a terminal, run
```
gconf-editor
```
Then navigate to "/apps/metacity/general" in the tree-menu, and then turn on the "reduced_resources" checkbox.  Note that this will affect other behavior as well (such as showing only the outline when you are resizing/moving the window).

---

### Post by bekok on 2006-06-24
Sweet, danx :)

---

