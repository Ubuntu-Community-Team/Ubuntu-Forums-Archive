---
title: "Compiz top panel transparency"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by ep3w on 2008-02-26
I know how to make the top panel transparent using compiz, my question is is there a way to make the panel transparent without making the text/icons transparent? Or is this not possible at the moment?

---

### Post by FuturePilot on 2008-02-26
I don't think this is possible now. I wish it was though.

---

### Post by ep3w on 2008-02-26
Maybe something to be mentioned for development?  Who develops it that it should be suggested to?

---

### Post by FuturePilot on 2008-02-26
You might be able to make a feature request [here]("http://forum.compiz-fusion.org/forumdisplay.php?f=91")

---

### Post by ep3w on 2008-02-26
Just messing around with it, the closest i can get is not using the transparency in compiz and just using the transparency when you right click the panel, but you are limited to using a single color and only looks best 100% transparent, at least in my opinion. For some reason I remember this option never working for me in the past as it left the clock/menus non transparent too...either and update must of fixed it or i changed something.

---

### Post by Islington on 2008-02-26
there may be a way dunno about the text but in CCSM>general options>opacity settings

you could add the filter :

```
(type=dock | desktop)
``` and set the opacity level to ~85?

---

### Post by ep3w on 2008-02-26
I was using that before, but using type=dock also makes AWN transparent, so I solved that with using type=gnome-panel but it still makes text/icons transparent along with it.

---

### Post by ph1 on 2008-02-26
You can also try making your own background image (a .png) for the top bar which has transparency built in and then set that as the background image.  I can imagine some cool effects would be possible this way.

---

### Post by fracturedmorals on 2008-02-26
Of course you could keep Y constrained, and use the panel's native "Fake" transparency without worrying about anything destroying the effect by getting underneath it.......

---

### Post by bekirserifoglu on 2008-03-09
You don't have to set the same transparency for both panels. you can use 

```
type=dock & title=Bottom Expanded Edge Panel
``` 

for the bottom panel and 

```
type=dock & title=Bottom Expanded Edge Panel
```

for the top panel. 

also check this out:

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

---

