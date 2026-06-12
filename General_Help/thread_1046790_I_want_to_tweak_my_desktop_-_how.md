---
title: "I want to tweak my desktop - how?"
date: 2009-01-21
forum: General Help
---

### Post by coiax on 2009-01-21
In short, I've got a simple idea for a desktop, using clean cool colours and such the like.

I want to be able to modify the transparencies of the panels (or find some sort of replacement), as well as modify the icon set to use the new colour scheme (or possibly just make them transparent and greyscale to use the colour of the wallpaper).

What can I install or modify or tweak to do this?

---

### Post by blackened on 2009-01-21
> **coiax said:**
> In short, I've got a simple idea for a desktop, using clean cool colours and such the like.

I want to be able to modify the transparencies of the panels (or find some sort of replacement), as well as modify the icon set to use the new colour scheme (or possibly just make them transparent and greyscale to use the colour of the wallpaper).

What can I install or modify or tweak to do this?

Panel transparency levels can be set by right-clicking an empty area of the panel, then selecting "Properties". In the subsequent dialog, select the "Background" tab, then toggle the "Solid Color" radio button and set the transparency level via the slider.

Icons can be modified using GIMP or the like. The icon files reside in either /usr/share/icons/*themename* or /home/*username*/.icons/*themename* depending on whether they were installed globally or locally. If you wish to edit icons that are in /usr/share... you'll need root privileges. Start whatever graphics program you're using by preceding it with *sudo* to accomplish this.

---

### Post by johnjohn2 on 2009-01-22
Install compiz and then hold alt while rolling the mouse wheel
Opacity needs to be enabled

[http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

Simple fix

john

---

### Post by blackened on 2009-01-22
> **johnjohn2 said:**
> Install compiz and then hold alt while rolling the mouse wheel
Opacity needs to be enabled

[http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

Simple fix

john

Agreed, very easy. If s/he is using compiz that is.

---

