---
title: "[SOLVED] Emerald Theme Manager NOT Changing"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by Antonio44 on 2008-04-15
Ok, 

I am trying to use mac4lin and i have installed the emerald theme. But it will not change i can highlight it but it will not apply it. Also once i changed my GTK theme my effects no longer work. But I need to know how to change my emerald theme HOW!?!?!

L.

---

### Post by Zorael on 2008-04-15
Are you sure you're running Emerald to begin with? The theme manager alone won't apply themes unless the decorator itself (emerald) is running. And do note that you need a window compositioner running to get it to work, such as Compiz (the "advanced desktop effects" compositioner).

Try entering the following in a terminal.
```
$ emerald --replace
```

If you end up without borders and things just go completely downhill, enter the following to return to your standard window decorator.
```
$ metacity --replace
```

Paste any error messages here.

---

### Post by Antonio44 on 2008-04-15
Thank you but I fixed it by accident actually:) I clicked on GL Desktop and the theme changed to what i had selected. I have no idea why but hey if it works don't knock it right?

---

### Post by Zorael on 2008-04-15
That actually makes sense. :>

Compiz is a window **compositioner** and adds 3D support to your graphical environment. It requires a window compositioning-aware **decorator** to draw titlebars and borders around windows - and likewise, compositioning-requiring decorators need a compositioner. Emerald is the default decorator, but Compiz comes with two more; gtk-window-decorator and kde-window-decorator. These are compositioning-aware clones of the standard "themers", so you can get 3D effects while still having the normal non-Emerald themes.

So, you used the Emerald theme manager to change which theme it was supposed to use, but it was never running. Metacity was; the standard Gnome window manager, which is a decorator as well as handling other behind-the-scenes window mechanics, such as keeping track of which windows have focus, etc. In the Compiz+decorator scenario, Compiz takes care of this.

Upon invoking Compiz (by running GL Desktop), it automatically started Emerald (since it's the default decorator), and you got both 3D effects and Emerald themes.

---

