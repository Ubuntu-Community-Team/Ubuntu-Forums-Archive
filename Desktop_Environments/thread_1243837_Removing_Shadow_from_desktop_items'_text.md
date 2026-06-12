---
title: "Removing Shadow from desktop items' text"
date: 2009-08-18
forum: Desktop Environments
---

### Post by TheNessus on 2009-08-18
Ok... anyway to remove the shadow that is normally present on desktop items (such as icons, files... etc) ? I use gnome.

thanks!

---

### Post by TheNessus on 2009-08-18
but does anyone know how to disable the shadow on the text of desktop items like icons and files? Sorry if this doesn't belong here; can't find anything on google either. Using ubuntu + gnome.    Many thanks

---

### Post by raymondh on 2009-08-18
> **TheNessus said:**
> but does anyone know how to disable the shadow on the text of desktop items like icons and files? Sorry if this doesn't belong here; can't find anything on google either. Using ubuntu + gnome.    Many thanks

Can you post a screenshot to visualize what you're referring to?

---

### Post by TheNessus on 2009-08-18
> **raymondhenson said:**
> Can you post a screenshot to visualize what you're referring to?

Any item on the desktop, it has a name, a text beneath its icon. excluding conky and screenlets etc of course. If you look closely you'd notice the text has a black shadow.

---

### Post by stinger30au on 2009-08-18
what shadow???

i dont have any one my desktop!
can u take a screenshot and show us?

---

### Post by TheNessus on 2009-08-19
Ok, so you see the difference between the conky text above, and the directory's name text below? the directory text stands out, it has a tiny shadow, whereas the conky is pure white.

---

### Post by raymondh on 2009-08-19
> **TheNessus said:**
> Ok, so you see the difference between the conky text above, and the directory's name text below? the directory text stands out, it has a tiny shadow, whereas the conky is pure white.

Have you tried with system > preferences > appearance > font TAB and it's various sub-sections like rendering, details, etc.?

---

### Post by TheNessus on 2009-08-19
> **raymondhenson said:**
> Have you tried with system > preferences > appearance > font TAB and it's various sub-sections like rendering, details, etc.?

Yups, it does not affect that at all. I tried gconf-editor as well but didn't find anything related to that shadow either

---

### Post by mcduck on 2009-08-19
> **TheNessus said:**
> Ok... anyway to remove the shadow that is normally present on desktop items (such as icons, files... etc) ? I use gnome.

thanks!

Sure.

First, you'll have to create a file called ".gtkrc-2.0" in your home directory. Then attach the following piece of code into that file:
```

style "desktop-icon"
{
  NautilusIconContainer::frame_text = 1
  text[NORMAL] = "#000000"
  NautilusIconContainer::normal_alpha = 0
  NautilusIconContainer::highlight_alpha = 255
  NautilusIconContainer::dark_info_color = "#444444"
  NautilusIconContainer::light_info_color = "#bbbbbb"
}
class "GtkWidget" style "desktop-icon"
```
Change the text[NORMAL]&#8211;color to change the icon name color. dark and light info colors are used for addition icon info, if you have any enabled..

When you are done, log out and back again to see the change. But be aware that this will also change the icon text colors in Nautilus windows, not only on the desktop. Change the background color/texture of Nautilus windows to dark or light one if necessary.

---

### Post by TheNessus on 2009-08-19
Worked like a charm, many thanks! :D

Now my desktop looks better: icons with text only now fit it perfectly with same-colored and fonted conky and rainlender

---

