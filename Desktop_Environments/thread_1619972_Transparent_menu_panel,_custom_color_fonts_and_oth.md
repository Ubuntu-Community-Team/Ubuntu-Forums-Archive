---
title: "Transparent menu panel, custom color fonts and other..."
date: 2010-11-12
forum: Desktop Environments
---

### Post by karogi on 2010-11-12
Hi guys, I need your help with my desktop improvement.




How can I edit menu panel font's color?

[[IMG]http://img130.imageshack.us/img130/6572/41983247.th.png[/IMG]]("http://img130.imageshack.us/i/41983247.png/")

How can I edit windows board key's effects/colors?

[[IMG]http://img600.imageshack.us/img600/7498/screenshot1iz.th.png[/IMG]]("http://img600.imageshack.us/i/screenshot1iz.png/")

---

### Post by karogi on 2010-11-12
bump.

---

### Post by karogi on 2010-11-13
bump.

---

### Post by TwoStep on 2010-11-13
Stop spam!!

---

### Post by stinkeye on 2010-11-13
For the font colors in the panel and menu use gnome-color-chooser.

For a transparent panel you need to edit the themes gtkrc file to stop it from using a background image for applets.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10032093&postcount=3[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10032093&postcount=3")

For the menu, if your using compiz open compizconfig-settings-manager and go to
*Accessibility > Opacity Brightness and Saturation* and add a new item to window specific settings
```
(type=Menu | PopupMenu | DropdownMenu)
```
with a value of about 90.
You can't set it too transparent because the text also becomes transparent.



...and yes you may be ignored if you bump in less than 24 hrs.Your new so probably didn't know.

---

### Post by karogi on 2010-11-13
thanks

---

