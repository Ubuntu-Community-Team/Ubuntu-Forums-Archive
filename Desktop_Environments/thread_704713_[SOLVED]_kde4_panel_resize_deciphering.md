---
title: "[SOLVED] kde4 panel resize deciphering"
date: 2008-02-22
forum: Desktop Environments
---

### Post by lunarcloud on 2008-02-22
Okay, trying to figure out how to resize the kde4 panel with little success. Here's what I've worked out so far.

1680 x 1050 Desktop's plasma-appletsrc
```

[Containments][2]
formfactor=2
geometry=0,994,1680,56
location=4
locked=false
plugin=panel
screen=0
transform=1,0,0,0,1,0,0,-1056,1
```

1280 x 768 Desktop's plasma-appletsrc
```

[Containments][2]
formfactor=2
geometry=0,712,1280,56
location=4
locked=false
plugin=panel
screen=0
transform=1,0,0,0,1,0,0,-774,1
```

So

```
geometry = 0**,** screenheight minus panelheight**,** width**, **panelheight
```and
```

transform = 1,0,0,0,1,0,0**,**screenheight+6**,**1
```

But changing these variables alone doesn't do it, the panel remains 56 pixels high, horrible on a widescreen like mine (1280x768).

Any Ideas?

---

### Post by inportb on 2008-02-23
I've tried that too, and it didn't work. Apparently... it's in the works: [http://vizzzion.org/images/blog/resizable-panel.jpg](http://vizzzion.org/images/blog/resizable-panel.jpg)

---

