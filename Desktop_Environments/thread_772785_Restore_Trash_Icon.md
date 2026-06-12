---
title: "Restore Trash Icon"
date: 2008-04-28
forum: Desktop Environments
---

### Post by zenon212 on 2008-04-28
I tried to change the trash icon on my current theme to one from another theme because I like everything in the current theme except for the trash icon.  But when I changed it I had not taken into consideration the fact that the icon has to be able to be variable based on whether or not something is in the trash and so I ignorantly set it to a fixed icon.  Once I made the realization that I did not know enough about how that icon works, it was too late.  Now my icon does not change based on whether it is empty or not and changing the custom icon theme or the theme in general does not make a difference.  Now I just want to put it back to the way it was an forget about it.

Does anyone know how to put it back the way it was so that my trash icon uses the trash icon from whatever icon theme is in place and so that it responds to content, or lack thereof?

---

### Post by zenon212 on 2008-04-29
Anybody know anything about how the trash icon works?

---

### Post by zenon212 on 2008-04-29
Well, I got it.  I ended deleting a lot of settings including the folder ~/.nautilus. I am pretty sure that is the one that did it.

---

### Post by spawn. on 2008-10-15
> **zenon212 said:**
> I tried to change the trash icon on my current theme to one from another theme because I like everything in the current theme except for the trash icon. But when I changed it I had not taken into consideration the fact that the icon has to be able to be variable based on whether or not something is in the trash and so I ignorantly set it to a fixed icon. Once I made the realization that I did not know enough about how that icon works, it was too late. Now my icon does not change based on whether it is empty or not and changing the custom icon theme or the theme in general does not make a difference. Now I just want to put it back to the way it was an forget about it.

Does anyone know how to put it back the way it was so that my trash icon uses the trash icon from whatever icon theme is in place and so that it responds to content, or lack thereof?

> **zenon212 said:**
> Well, I got it.  I ended deleting a lot of settings including the folder ~/.nautilus. I am pretty sure that is the one that did it.

If anyone else is having trouble with this, do not go deleting files without knowing what you're doing. To solve this problem visit the link to this thread:  [http://ubuntuforums.org/showthread.php?t=812610](http://ubuntuforums.org/showthread.php?t=812610)

---

### Post by bsmith1051 on 2008-12-21
Good call!  I'd give you a Thanks but the option is missing?

Here's the solution:
- load the Gnome **Configuration Editor** (similar to Windows Registry Editor)
  it should be under Applications > System Tools > Configuration Editor
- dig down to the section **/apps/nautilus/desktop**
  and enable the "Trash_icon_visible" checkbox

Doesn't restore the original Trash icon on the panel (still working on that?) but it does restore a useable copy on the desktop.

**UPDATE**
I'll bet its one of the settings under **/apps/panel/default_setup/applets/trashapplet** but I can't figure-out which...

---

### Post by bsmith1051 on 2008-12-21
**SOLVED**
Actually, I solved my problem but I'm not sure that's the same as your prob.  I had right-clicked on my Trash icon (enroute to Emptying it) but accidently clicked on Remove From Panel.  Ooops, gone!

The solution:
[LIST=1]
[*]close all/most of your windows so that you can see blank 'panel' along the bottom of the screen
[*]right-click in the blank area and select Add To Panel
[*]scroll down the list of applet and select Trash
[*]Fixed!  You might also want to Move it and/or Lock To Panel
[/LIST]

---

