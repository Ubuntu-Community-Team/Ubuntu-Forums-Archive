---
title: "My windows don't have any borders"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by ubuntu_jazzbach on 2007-08-22
Hi !!!

I've installed compiz fusion and I've tried it. The thing is that, now that I want to work without compiz fusion, none of the applications have it's border (the title border) and now I can't move them. 

How can I get back the border of the windows ??

---

### Post by GuiPoM on 2007-08-22
Did you try to add :

```
Option          "AddARGBGLXVisuals"      "true"
```

in Device section of your xorg.conf ?

---

### Post by ubuntu_jazzbach on 2007-08-22
WWOOWW !!! IT WORKED !!! Thanks a lot !!!

---

### Post by floogy on 2007-08-22
> Option          "AddARGBGLXVisuals"      "true"

I had
> Option          "AddARGBGLXVisuals"      "[COLOR="Red"]T[/COLOR]rue"

could it be, that several issues I had, came from the capital 'T'?

---

