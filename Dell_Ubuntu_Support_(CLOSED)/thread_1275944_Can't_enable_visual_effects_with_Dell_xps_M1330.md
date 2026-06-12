---
title: "Can't enable visual effects with Dell xps M1330"
date: 2009-09-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by oranxess on 2009-09-26
Hey there , I downloaded  the normal desktop edition of Ubuntu and installed it via Wubi in windows Vista . 
now when I right click to enable the visual effects I see "searching for new drivers or something like that" then it goes away .. also when I go to hardware-manger I can't see any Nvidia drivers like Ubuntu 8.10 
what do you think I should do to install the drivers or enable the effects ? Thank you

---

### Post by yeats on 2009-09-26
I'm pretty sure you're dealing with this:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

You can discover your graphics card information by typing this into a terminal (Applications -> Accessories -> Terminal):

```
lspci | grep VGA
```

---

### Post by oranxess on 2009-09-26
Thank you ! I manged to get it done :) :P

---

