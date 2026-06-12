---
title: "[Gutsy, GTK] 13px white border around popup menus"
date: 2007-10-20
forum: Desktop Environments
---

### Post by harrison.caudill on 2007-10-20
Description:
GTK popup menus present themselves with a surrounding 13-px white border.  The border is somewhat annoying, though does not interfere with most functionality.  In a few cases, however, the border does actually hide useful information.  Examples shown in the links below.

[ In GNOME ]("http://picasaweb.google.com/harrison.caudill/Misc/photo#5123520640420000802")
[ In Firefox ]("http://picasaweb.google.com/harrison.caudill/Misc/photo#5123520640420000818")

Reproduction Steps:
Unknown

Attempted Fixes:
I've searched through the Gnome documentation, as well as the various fields in gconf-editor, to no avail.

Environment:
Ubuntu Gutsy
Xgl 1.1.99.1~git20070727-0ubuntu3
beryl 0.2.0(manually built/installed as the ubuntu beryl package lacks the beryl-xgl binary)
emerald 0.2.1 (manually built/installed as emerald was problematic)
Gnome 2.18.3ubuntu2

If any information is missing, please let me know and I'll track it down.  Any advice would be appreciated -- even a new tree to bark up would be useful.

---

### Post by bakster on 2007-10-20
I had this problem too.I think it's a xgl bug.Open up emerald theme manger and try to reduce shadow size for current emerald theme,or try to use gtk-window-decorator.

---

### Post by Innovator on 2008-01-21
I seem to be having this exact same problem w/ Gutsy's built-in Compiz Fusion.  The only work-around I have is to unselect and reselect my custom theme in the Gnome Appearance menu everytime I boot into Ubuntu.

---

### Post by dgcoffman on 2008-02-26
This appears to be a problem with certain video card drivers (ATI's 8.02, I believe) that causes Compiz window shadowing to render incorrectly. 

A workaround is to open compizconfig settings manager and under the "Window Decoration" menu set "Shadow windows" to "none" -- of course this means no windows or menus get dropshadows.


EDIT: 
It looks like simply changing the "Shadow windows" value from "any" to "any !dock !menu" (minus the quotes) is a better solution with nearly identical results except you get to keep shadows where they should be.

Mark this SOLVED if it helps =)

---

