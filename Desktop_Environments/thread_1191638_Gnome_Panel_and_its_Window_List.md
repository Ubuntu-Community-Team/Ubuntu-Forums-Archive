---
title: "Gnome Panel and its Window List"
date: 2009-06-19
forum: Desktop Environments
---

### Post by hotkoi on 2009-06-19
Hey guys,

I want to enlarge the icons and  remove the text or at least reduce the width of the Window List's elements.

I read several blogs and forum posts and know that XFCE's Window List is what I want. I also found a package but didn't manage to make it usable for my gnome desktop.

As you see can on the screenshot ([http://img220.imageshack.us/img220/7138/screenshot2d.png](http://img220.imageshack.us/img220/7138/screenshot2d.png)), the icon sizes differ, depending on the panel element (I increased the panel's height to 48).

Question: It would be easy if I could define a global icon size for all icons of all items on the panel and additionally define a smaller width for the Window List's elements. But it seems that any element uses its own variables... So does anyone know where I can change these values or are they not changeable?

Regards and thanks for your time,
Erik

---

### Post by Fzang on 2009-06-19
The icons that won't change is probably because they're 16px and won't go any higher. You could go into the icon theme and find the 16px application icons and swap them with scalable icons, then they will grow with the panel.

---

### Post by UbuntuNerd on 2009-06-19
you can get use the "window selector" instead of "window list" from the add to panel.
"window selector" lets you choose between open windows using a menu instead of buttons, it would minimize all those open windows in your panel.

---

### Post by hotkoi on 2009-06-19
mmm... in MS Windows this is a thing of 3 clicks and a reboot of course :D

does really noone know where the window list gets its parameters from?

edit: @fzang: if you choose a custom picture for the 2009 linux mint menu (2nd update of today at about midday, don't know how far they are meanwhile ;))  which is like... 1000px in width and height, the menu preferences window fits to this proportions. so i dont think that a window list from 2002 checks if an icon would look good with higher values for width and height ;)

---

