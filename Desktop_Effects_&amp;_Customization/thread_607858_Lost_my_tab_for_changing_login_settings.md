---
title: "Lost my tab for changing login settings"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by bcdeck on 2007-11-09
The System -> Administration -> Login tab has gone missing from my menus. I have tried editing menus to see if it's unchecked, but it's not. 

I'm running Gutsy and I have been dabbling in Kubuntu -- I have kubuntu and Gnome icons in my start menus now. 

Is there some other place I can look to get to my login settings?

---

### Post by TadH on 2007-11-09
alt+f2 tpe in gconf-editor
go to apps>panel>applets>applet0 and make sure it says applications:/

that should work

---

### Post by TadH on 2007-11-09
if that isnt exactly what u need look around under the panel in gconf editor you will find it there

---

### Post by bcdeck on 2007-11-09
> alt+f2 tpe in gconf-editor
go to apps>panel>applets>applet0 and make sure it says applications:/

Check.

didn't find it under the panel in gconf editor, but then I looked at the list that came up with alt-F2, and found it. It's the KDE version of login settings.

---

### Post by TadH on 2007-11-09
good job :)

---

