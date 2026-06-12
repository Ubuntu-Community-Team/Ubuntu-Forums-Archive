---
title: "WBar real transparency possible?"
date: 2009-04-29
forum: Desktop Environments
---

### Post by vickoxy on 2009-04-29
Hi,
 i just want to know is there any way to activate real transparency by wbar, but whitout activating fusion/metacity compositing manager/xcompmgr? Only with gnome metacity desktop (Dell Mini9, Ubuntu 8.04)

Subquestion: is there any launch/bar dock with real transparency that doesn´t need any additional 3D effects activated? (i tried AWN, Cairo-dock...)

---

### Post by vickoxy on 2009-04-29
No one knows?

---

### Post by Sarai the Geek on 2009-04-29
Someone else may have a more exact answer, but I will say that you may not be able to find anything. If you want eye candy, you really need compiz.

---

### Post by vickoxy on 2009-04-29
is there any usable dock running whitout 3d effects?
thanks

---

### Post by damis648 on 2009-04-29
Unless the bar supports compositing (with you need for real transparency) then it cannot be truly trasparent. Try opening a terminal and entering in:
```
gconftool --set -t boolean /apps/metacity/general/compositing_manager true
```
in order to set metacity to be a compositing window manager. If this doesn't make the bar truly transparent, there is likely nothing you can do unless there is some option in the settings of the program.

EDIT: Try gnome-do with the Docky theme if you are looking for something else. It works great as a dock and a launch / search panel. You will need compositing enabled so first run the above command.

---

### Post by vickoxy on 2009-04-29
I tried with compositing awn and cairo-dock. Both work fine (cairo maybe better) but there are some glitches when i switch from tab to tab/applications.
I have dell mini 9 with Ubuntu 8.04. LPIA and i look for some launch bar that has auto hide (tried to use one panel as launch bar, but there is always 1 pixel left to be seen and that is annoying).

I do not need transparency (as background i could add some picture) but i am affraid that whitout transparency, this area around icons would be pretty big...

---

### Post by damis648 on 2009-04-29
Again, have a look at gnome-do's Docky. It should perfectly fit your needs. If your only problem is that you need the panel to vanish completely, open gconf-editor with Alt+F2 and head to /apps/panel/toplevels and each panel you have will be listed in that folder as separate folders. Head to the one you want (or all) and change the auto_hide_size to 0. :popcorn:

---

### Post by vickoxy on 2009-04-29
> **damis648 said:**
> Again, have a look at gnome-do's Docky. It should perfectly fit your needs. If your only problem is that you need the panel to vanish completely, open gconf-editor with Alt+F2 and head to /apps/panel/toplevels and each panel you have will be listed in that folder as separate folders. Head to the one you want (or all) and change the auto_hide_size to 0. :popcorn:

Tried all that, but on small dell´s screen that 1 pixel is always visable. But, docky needs some compositing/3D?

---

### Post by Sarai the Geek on 2009-04-29
> **vickoxy said:**
> Tried all that, but on small dell´s screen that 1 pixel is always visable. But, docky needs some compositing/3D?

Yeah, you definitely need a compositing window manager for Docky. As a test I just ran it without compiz enabled- it made half my screen black.

---

### Post by damis648 on 2009-04-29
> **Sarai the Geek said:**
> Yeah, you definitely need a compositing window manager for Docky. As a test I just ran it without compiz enabled- it made half my screen black.

Like I said, you can enable compositing in metacity (without compiz) by either using gconf-editor or running the following:
```
gconftool --set -t boolean /apps/metacity/general/compositing_manager true
```

---

### Post by vickoxy on 2009-04-30
> **damis648 said:**
> Like I said, you can enable compositing in metacity (without compiz) by either using gconf-editor or running the following:
```
gconftool --set -t boolean /apps/metacity/general/compositing_manager true
```

I did that-but there are still some glitches when i using it. So, that is why i ask is it possible to do something whitout activating any other options....?

---

### Post by vickoxy on 2009-04-30
> **vickoxy said:**
> I did that-but there are still some glitches when i using it. So, that is why i ask is it possible to do something whitout activating any other options....?

I did what you recomended. Cairo-dock works really good and fast. Well, these glitches i´ll have to tolerate, otherwise no dock. Still, the little mini 9 is enough fast, and these glitches aren´t slowing the system. Thanks for helping me:P!

---

