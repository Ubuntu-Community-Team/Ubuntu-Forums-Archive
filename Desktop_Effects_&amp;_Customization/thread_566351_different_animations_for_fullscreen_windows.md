---
title: "different animations for fullscreen windows"
date: 2007-10-03
forum: Desktop Effects &amp; Customization
---

### Post by Chymera on 2007-10-03
ok, so i like the "burn" animation a lot, hence i use it as the effect for opening and closing windows. However, when windows are opened or closed in fullscreen mode, the animation gets quite buggy (seeing as the particle size constant translates into percent values of the window size). So i would like to tell compiz fusion to open fullscreen windows with some other effect. 
How can i make this differentiation? can i do that by using some special syntax in the type entries corresponding to the animations? do i have to use the window rules plugin?

---

### Post by Chymera on 2007-10-11
bump...

---

### Post by Forlong on 2007-10-11
I don't think that's possible. You can only differentiate between applications, window types etc. (see [here](http://wiki.compiz-fusion.org/WindowMatching#identify))

---

### Post by Chymera on 2007-10-12
> state: Is the window maximised, staying on top, sticky, or something else?

    * Choose one: modal, sticky, maxvert, maxhorz, shaded, skiptaskbar, skippager, hidden, fullscreen, above, below, or demandsattention

Shouldn't I be able to get the behavior I want through the state criterion?

---

### Post by Lord Illidan on 2007-10-12
Yes.
Look at mine, for example. state=maxvert is done when a window is full screen, so full screen windows close with a different animation.

---

### Post by Forlong on 2007-10-12
Nice. Didn't know that.

---

### Post by Chymera on 2007-10-12
[http://img444.imageshack.us/img444/3029/screenshot31xt9.png](http://img444.imageshack.us/img444/3029/screenshot31xt9.png)

... yes, well that's exactly what I did (see my settings in the screenshot above)
But compiz seems to not get it.... every window still closes with the burn effect (yes I have the regex plugin enabled)

---

### Post by Lord Illidan on 2007-10-12
Try putting this : ```
 (type=normal|utility)&!(name=gnome-screensaver)&!(state=maxvert)
```
Or this : 
```
(type=normal|utility)&!(name=gnome-screensaver)& !((state=maxvert)|(state=maxhorz)|(state=fullscreen))
```

---

### Post by Chymera on 2007-10-14
10x, worked for me... But i still have trouble with nautilus opening in non-fullscreen windows, which are about the same size as fullscreen windows... is there any way to specify the stat eo a window through smth like  state>=1000px or >=95% ?

---

