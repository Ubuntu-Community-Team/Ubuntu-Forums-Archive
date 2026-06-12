---
title: "Why do my Nautilus boarders look crappy?"
date: 2011-12-05
forum: Desktop Environments
---

### Post by IanVaughan on 2011-12-05
Have a look at the attached file.
It shows how most things are setup the way I want, window boarders etc.
But the menu on the desktop and file exploding via Nautilus.
Any clues as to what needs changing?
(If I create a new user its all nice for them!)

---

### Post by Frogs Hair on 2011-12-05
Run the following command and then check nautilus to see if the theme is displaying properly .```
nautilus -q
```

---

### Post by IanVaughan on 2011-12-07
> **Frogs Hair said:**
> Run the following command and then check nautilus to see if the theme is displaying properly .```
nautilus -q
```

Hay, that did it! Thanks.

Running it stops right-click on desktop from working until I reopen a Nautilus window (like my home)

So, whats the problem/solution then?

---

### Post by Frogs Hair on 2011-12-07
In pre 11.10 versions of Ubuntu a similar problem was caused by gnome-settings-deamon. See the section on nautilus crashing at the link . 

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

