---
title: "Where are the window decorations for Compiz Fusion?"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by volksolwagen57 on 2007-07-03
I installed compiz fusion and everything works great. all the effects are working and i love it. the only thing it's lacking are window decorations. i still want the transparent windows that my old emerald and beryl setup used to have. how do i do this?
thanks for your help in advance.

---

### Post by Megaqwerty on 2007-07-03
You can still use emerald with compiz-fusion. As for window trasparency, I'd check ccsm, or if you mean just turning windows transparent, the combination of Alt+Mousewheel will change the transparency of a window.

---

### Post by joep on 2007-07-03
Click System  Preferences  CompizConfig Settings Manager  should be on the list. I just use Windows decorations under Effects and it works.

---

### Post by Monstroxus on 2007-07-03
If you want to use an emerald theme, just go to the emerald theme manager as usual, click the theme of your choice... most likely nothing will happen, that's ok, but then... you have to make a launcher with the following command: emerald --replace

Click on this launcher when you have Compiz Fusion running. The theme you picked earlier will be applied. At least this worked for me.

---

### Post by walkerk on 2007-07-03
just add this to session manager (System > Preferences > Sessions)
```
sleep 10 && compiz --replace -c emerald
```

---

