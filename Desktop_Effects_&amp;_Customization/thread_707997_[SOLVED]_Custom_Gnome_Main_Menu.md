---
title: "[SOLVED] Custom Gnome Main Menu"
date: 2008-02-25
forum: Desktop Effects &amp; Customization
---

### Post by ChaoticVengeance on 2008-02-25
I've been looking to customize my panel menu, and decided to use the single-click main menu button as opposed to the three-tiered applications-places-system bar.  The problem I'm having is that "places" and "system" exist on the menu and I no longer need them.  They are cluttering up my menu, but I can't seem to remove them.  I've searched a wide number of forums and I've never seen an answer that works.  Is it possible to remove "system" and "places" from the menu?  And if do, how do I go about doing it?
     On a sidenote, I realize I'm making my desktop look a little more like a default KDE, and switching to kubuntu would probably make it *look]* the way I want.  That said, I prefer the gnome DE for its streamlined simplicity..  It just feels better to me.
     Any help or information would be greatly appreciated.  Thanks

~Craig

---

### Post by ChaoticVengeance on 2008-02-25
Yarg...I posted in the wrong channel...

---

### Post by PhrankDaChickenGeek on 2008-02-25
Yup - 
Open a terminal
```
gconf-editor
```
Expand "Apps" -> "Panel" -> "Objects"
Find the Obejct with an object type of "Menu Object" (This is the single-click main menu)
Check the "Use_Menu_Path"
This may/may not be want you want, but it sounds like it

---

### Post by ChaoticVengeance on 2008-02-25
That was exactly what I was looking for,  Now that I think about it, I've seen that answer before, but the description made it out to be something different in my mind.

Many thanks.

~Craig

---

