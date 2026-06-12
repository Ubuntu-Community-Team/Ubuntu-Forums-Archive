---
title: "strange windows behaviour"
date: 2009-09-19
forum: Desktop Environments
---

### Post by WDYSUN on 2009-09-19
Dear Friends,

I have Ubuntu 9.04 on my system. I like minimal graphical setups, so my "visual effects" is set to "none". With this setting I have just one problem, when I minimise windows they go down with the appearence a series of black shrinking rectangle. Is this behaviour a regular thing? Can I fix it in some way?

Thanks for your help
Pierre

---

### Post by scrooge_74 on 2009-09-20
Could be a driver related issue with your video card

---

### Post by coldfusion1313 on 2009-09-20
> **WDYSUN said:**
> 
when I minimise windows they go down with the appearence a series of black shrinking rectangle.

No that is normal, it happens to me when I have no desktop effects. On the other note, why do not you have desktop effects enable, they are really sweet and make your computer look cool. :)

---

### Post by drs305 on 2009-09-20
I think running this command will stop the effect you are mentioning. On my machine, what I see as a shrinking rectangle occurs very quickly - almost unnoticeable to me. Of course, it disables more than just this animation, but you can try it:

```

gconftool-2 --type bool --set /desktop/gnome/interface/enable_animations 'false'	

```

You can reset it by changing the value back to 'true' or opening gconf-editor and going to the applicable setting:
```

gconf-editor /desktop/gnome/interface/enable_animations

```

If the above is too general, you could search in gconf-editor for "animations" and see if there is a more targeted setting.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by WDYSUN on 2009-09-21
thanks a lot! worket brilliant!!!

Pierre

---

