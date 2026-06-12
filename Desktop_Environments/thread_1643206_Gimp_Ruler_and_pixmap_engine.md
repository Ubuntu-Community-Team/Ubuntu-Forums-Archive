---
title: "Gimp Ruler and pixmap engine"
date: 2010-12-11
forum: Desktop Environments
---

### Post by bvc on 2010-12-11
I am trying to update a few pixmap engine themes and can't get the ruler to display/work without corruption in gimp. Works in Inkscape. The two themes have have tried are Scutum
[http://gnome-look.org/content/show.php/Scutum?content=58705](http://gnome-look.org/content/show.php/Scutum?content=58705)

and Onux
[http://gnome-look.org/content/show.php/Onux?content=58118](http://gnome-look.org/content/show.php/Onux?content=58118)

Any help is appreciated.

---

### Post by bvc on 2010-12-12
SkiesOfAzel on gnome-look helped me out. What is needed for gimp is```
widget "*GimpRuler" style "ruler"
```

---

