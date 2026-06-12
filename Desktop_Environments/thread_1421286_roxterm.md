---
title: "roxterm"
date: 2010-03-04
forum: Desktop Environments
---

### Post by dzon65 on 2010-03-04
Does anyone know how to make roxterm to open without the (openbox)windowborder?I can set the scrollbar,menu  not to show when opened but not the windowborder.

---

### Post by VCoolio on 2010-03-04
That's done by your window manager. If you use compiz, use the "window decoration" plugin; there is an entry where you can specify what windows to decorate; make an exception for roxterm, like
!(class=Roxterm)
or if you don't want each roxterm window to be undecorated, run it like
roxterm --class=blah or roxterm --name=blah, and use blah for the exception line.
If you don't use compiz, check your window manager's settings or try devilspie.

---

### Post by dzon65 on 2010-03-04
Thanks V!Will check it out.
Kind regards,J.

---

### Post by warfacegod on 2010-03-04
Maybe try increasing the transparency. Might not get rid of the border but it still might look cool. (Not that it doesn't now.)

---

