---
title: "MATE: how to move window buttons to the left?"
date: 2012-05-23
forum: Desktop Environments
---

### Post by Nickolai_Leschov on 2012-05-23
I have installed Ubuntu 12.04 LTS, but I couldn't get used to any of the supplied GNOME environments, so I installed MATE.

How do I move window buttons from right to the left in MATE?

---

### Post by Frogs Hair on 2012-05-23
You should be able to move the window buttons in the configuration editor , but I don't know the application name in Mate . That was how it was done in Gnome  2  before Ubuntu Tweak.

---

### Post by ronc on 2012-05-25
```
mateconftool-2 --set /apps/marco/general/button_layout --type string "close,minimize,maximize"
```

from [http://forums.mate-desktop.org/](http://forums.mate-desktop.org/)

---

### Post by MadmanRB on 2012-05-25
> **Frogs Hair said:**
> You should be able to move the window buttons in the configuration editor , but I don't know the application name in Mate . That was how it was done in Gnome  2  before Ubuntu Tweak.

I wonder if ubuntu tweak will work mate, I never tried it but I say go for it it cant hurt as it will be easier then the mate configuration tool.

---

### Post by zombifier25 on 2012-05-26
> **MadmanRB said:**
> I wonder if ubuntu tweak will work mate, I never tried it but I say go for it it cant hurt as it will be easier then the mate configuration tool.
I would say... nope. UT does not have that feature yet, and it's very unlikely that it will have anytime soon, since it's **Ubuntu** Tweak.

---

### Post by Nickolai_Leschov on 2012-05-27
Thanks, ronc! mateconftool-2 works.

---

### Post by TinMan77 on 2012-08-20
> **ronc said:**
> ```
mateconftool-2 --set /apps/marco/general/button_layout --type string "close,minimize,maximize"
```from [http://forums.mate-desktop.org/](http://forums.mate-desktop.org/)


I did this and it worked, now to do i un-do it?

---

### Post by DoubleClicker on 2012-08-20
> **TinMan77 said:**
> I did this and it worked, now to do i un-do it?

I don't know why anyone would want to undo putting the buttons in the correct order :P

But if you really want to.
```
mateconftool-2 --set /apps/marco/general/button_layout --type string "menu:minimize,maximize,close"
```

The general rule is:
Left side items are separated by a comma.
A colon separates the left side items from right side items.
Right items are separated by a comma.

---

