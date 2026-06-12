---
title: "Gnome panel icons are messed up"
date: 2006-10-12
forum: Desktop Environments
---

### Post by SebMKd on 2006-10-12
After a simple updated of my xorg.conf (added Horz and Vert refresh rates), I found my Clock and ON/OFF button in the middle of the top panel and the trash bin has also moved to the middle of the bottom panel!:-k 

Has Xorg anything to do with the Gnome panels?
How can I replace those icons?

Thanks!

---

### Post by meng on 2006-10-12
Strange. I would try right-click on the icon, Move, move it to where you want, then right-click again and Lock.

---

### Post by SebMKd on 2006-10-12
Can't move them with right click! :(
I've search Gnome.org forums as well and didn't find any thread talking about the Gnome default icons position (Sound, Clock, OFF, Trash)...
It's not dramatic, however, I'd like to at least move the trash to get more shortcuts on the bottom panel!

Thanks anyway!

---

### Post by meng on 2006-10-12
If you can't move them, make sure they're not Locked to Panel (same technique, right click on the icon). If they're Locked, you won't be able to select Move from the menu.

---

### Post by FizDev on 2006-10-12
I believe you can reset the Gnome settings by doing this :
Log out
Press Ctrl+Alt+F1
Log in (console), then remove .gnome and .gconf in your home directory:
```
rm -rf .gnome
```
```
rm -rf .gconf
```

Then Gnome will regenerate automatically theses files, everything should be alright after (I think, not sure)

---

