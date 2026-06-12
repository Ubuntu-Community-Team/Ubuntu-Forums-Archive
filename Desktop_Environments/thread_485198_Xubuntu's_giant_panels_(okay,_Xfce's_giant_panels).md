---
title: "Xubuntu's giant panels (okay, Xfce's giant panels)"
date: 2007-06-26
forum: Desktop Environments
---

### Post by timzak on 2007-06-26
I just started messing with Xubuntu recently on a spare computer and I'm not crazy about how thick the top and bottom panels are.  I know you can resize them, but when I did this, I found the icons within the panels would automatically resize too--such that if you get the panel about the same thickness it would be in Ubuntu (Gnome), the icons are so small as to be nearly invisible.  It seems as if there must be x pixels between the icon and the panel borders.  I'd like to be able to narrow the panels down without shrinking the icons, so that the icon gets as close to the borders of the panel as possible.

Can this be done?

---

### Post by kadath on 2007-06-26
I'm not really sure, but this may have to do with the GTK theme. You might want to ask about this on the Xfce forum: [http://forum.xfce.org/](http://forum.xfce.org/)

---

### Post by ugm6hr on 2007-06-27
I think it may be because the icons (e.g. /use/share/pixmaps/firefox.png) has some *transparent* space below and to the right of the *picture* within the icon image file.

So, xfce obviously has to resize the transparent space as well, because it can't tell the difference.

If you want to ness about with it - you could try resaving the panel icons used (with different file names), and edit them  in GIMP to remove the transparent areas (but keeping them square).  The just change the "properties" of the launcher to direct it to the newly created icon.

EDIT: I've just tried this - and it resizes a lot more than I would expect.... so dunno.

---

### Post by timzak on 2007-06-27
Thanks guys.  I was just curious.  It's not a big enough deal that I'm going to try and fix it.  I just wanted to know if there was some easy, obvious fix that I was missing.  I guess if you move everything to one panel, then delete the other panel, they don't take up quite so much of your screen.

---

