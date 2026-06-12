---
title: "ROX-Filer  question"
date: 2009-04-08
forum: Desktop Environments
---

### Post by O-pos on 2009-04-08
Hi,

I installed rox-filer and I like the way it functions, but I could not figure out how can I "import" settings which file type should be opened by which application. I know that it is possible to do it manually for each file type but it's painful to do it for every type of files I have. Maybe anyone had better idea?

Thanks

---

### Post by kerry_s on 2009-04-09
i don't think so, rox does mime types different than others.
look in ~/.config/rox.sourceforge.net/

---

### Post by Mark76 on 2009-04-09
It's possible to set a particular application to run a particular file type by right clicking on the file, then clicking on "File ' '" from the menu, then choosing "Set Run Action" from the sub-menu and then dragging and dropping the appropriate bin file from /usr/bin into the little box that pops up.

You can set alternative actions for each file type by right clicking on the file again, clicking on "File...", choosing "Customize Menu from the sub-menu and then dragging and dropping bin files into the filer window that pops up as before (forex: Gthumb for viewing an image would be the main run action for jpgs and other graphics files, whilst for editing you'd use GIMP as an alternative action).

Hope that's clear.

To set a run action to cover all possible versions of a particular mime type choose the Set Default for All option in the Set Run Action dialog box

---

### Post by kerry_s on 2009-04-09
:lolflag:
that's what he said he didn't want to do.

he wants it like other file managers were there is already a default program selected and all he has to do is click on it, then if he don't like it he can change it. think pcmanfm, thunar, nautilus, etc...

---

