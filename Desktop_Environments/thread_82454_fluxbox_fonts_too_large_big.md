---
title: "fluxbox fonts too large big"
date: 2005-10-26
forum: Desktop Environments
---

### Post by ahh_dee on 2005-10-26
I installed fluxbox fine but i have an issue with the fonts being to big in programs like oowriter, firefox, gedit and evolution. the themes font sizes are fine but its the programs.  does anyone know how to change this?

---

### Post by borispierkov on 2008-05-15
Try this if you are using nvidia :)

[http://aaron.instantspot.com/blog/2007/09/10/Get-rid-of-those-huge-fonts-in-Fluxbox](http://aaron.instantspot.com/blog/2007/09/10/Get-rid-of-those-huge-fonts-in-Fluxbox)

It worked for me :)

---

### Post by kerry_s on 2008-05-15
editor ~/.gtkrc-2.0
put:
**gtk-font-name="Sans 10"**

adjust size & font as needed. i like mine small and dark "sans bold 7".

for ooo, tools> options> view, user interface change scaling, lower will make the fonts smaller it will only go 80%.

---

