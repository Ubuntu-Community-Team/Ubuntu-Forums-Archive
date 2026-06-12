---
title: "Enable transparency for menu applet in gnome-panel"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by Cerberus108 on 2008-01-06
Hello, some days ago I found out that the menu applet (on the left in gnome-panel) and any similar applet aren't transparent. I tried to customize my desktop with a dark theme, and I achieved this (using the macmenu-applet): [(this screenshot is quite big)]("http://cerberus108.files.wordpress.com/2008/01/bw.jpg"). It's pretty annoying that solid color behind the applet: does anybody can tell me if I can enable somewhat a transparency, please? Thanks in advance! (And sorry for any bad english :lolflag:)

---

### Post by Ub1476 on 2008-01-06
Open CCSM>General>Opacity settings>Add>name=gnome-panel>about 1-99 opacity (you choose).

And set the panel to use GTK theme, not custom color.

EDIT: If you do not want the dropdownmenu for Apps/Places/System to be transparent as well, the name should be "type=dock".

---

### Post by Cerberus108 on 2008-01-09
Thanks for the help, but I figured out that the theme is buggy: I tried the mac4lin, and it worked.. Seems I'll have to going down into the source, to get how to do enable transparencies. :)

---

