---
title: "GNOME Main Menu icon"
date: 2008-12-06
forum: General Help
---

### Post by EvilRick on 2008-12-06
I like the GNOME Main Menu but don't like the tiny icon.  I created this just to add something to it.

It's 80x20 pixels with a transparent background.  Nothing craptacular, but it's something.

You have to use gconf-editor and go to the apps/panel/objects section.  There's objects_x (where x= a number) sub-section(s) and one of those is for your menu.  Check the box that says "use_custom_icon" and edit the "custom_icon" to show the path to the icon itself.

---

### Post by linkmaster03 on 2008-12-06
Thanks dude, I've been wanting to change that icon for so long, but I was too lazy to search for how to do it. I stumbled upon this post today and finally did it.

---

