---
title: "Xfce panel text size - (Xubuntu 6.06.1)"
date: 2006-10-10
forum: Desktop Environments
---

### Post by Zerksis on 2006-10-10
When first installed (clean install) the Xfce panel text is a nicely proportioned size, as is the panel drop down menus.

After checking *sub-pixel hinting*, in the *User Interface Prefs*, the panel text size and the drop down menu text size
then becomes very small.
It does not return to it's previous size when unchecked ?

*Panel Mgr* -> *Help* gives *Documen... Manuals* -> *Panel*
but Panel file is not available ?

Should enabling sub-pixel hinting change the text size ?
Selecting LCD panel in Ubuntu Gnome does not change font size.

Any Xubuntu/Xfce wizard able to point me in a suitable direction to set panel text size?

Thanks.

---

### Post by markster23 on 2006-11-26
having the same problem...

---

### Post by markster23 on 2006-11-26
okay fixed..
open up a terminal
type sudo mousepad [B]/home/<username>/.gtkrc-2.0
look for the line:[/B][FONT=monospace] [/FONT]gtk-font-name="DejaVu Sans 9"
change that to whatever to reflect the font and font size in ur gtk theme......

---

### Post by je m'ennuie on 2006-11-27
Look at post #4 in this thread :
[http://www.ubuntuforums.org/showthread.php?t=246111&highlight=xubuntu+fonts+size](http://www.ubuntuforums.org/showthread.php?t=246111&highlight=xubuntu+fonts+size)

---

