---
title: "Icon highlight efect ?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by Vilius on 2006-07-05
Hi,
I'm talking about icon highlight efect, which we can see in nautilus app, gnome panel app, desktop - when we mouseover on them. Actually i want to remove this efect, but if it is not possible I'd like to now what peace of software is responsible for this feature - gnome, nautilus, metacity or something else ?

thanks
Vilius

---

### Post by 23meg on 2006-07-05
It's part of Nautilus. You'll probably have to modify the source code to remove it.

---

### Post by mcduck on 2006-07-05
At least for Gnome panel you can remove it wirh gconf-editor (Configuration Editor in menu, run 'gconf-editor' in terminal if you can't find it). I think the correct key was something like apps/panel/global/enable_animations or something. I'll have a look when I get home from work. :)

There might also be something under apps/nautilus..

---

