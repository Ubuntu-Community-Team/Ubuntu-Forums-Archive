---
title: "Nvidia 8600GTS Desktop Effects/Compiz/Beryl"
date: 2007-09-12
forum: Desktop Effects &amp; Customization
---

### Post by PTemplar on 2007-09-12
I recently got an EVGA Nvidia 8600GTS video card. And when I try to use the desktop effects with Compiz OR Beryl, my frames and borders go missing.

[http://i220.photobucket.com/albums/dd281/PTemplar/Screenshot-1.png?t=1189650289]("http://i220.photobucket.com/albums/dd281/PTemplar/Screenshot-1.png?t=1189650289")

---

### Post by smartboyathome on 2007-09-12
Try running this in a terminal and post the output (while compiz is running):
```
gtk-window-decorator --replace
```

---

### Post by PTemplar on 2007-09-15
Nothing happens =\

---

### Post by dougfractal on 2007-09-15
I've found that this problem can be caused by a ccsm error


ccsm
>preferences>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4

---

