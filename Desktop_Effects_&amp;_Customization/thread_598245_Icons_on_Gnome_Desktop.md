---
title: "Icons on Gnome Desktop"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by Roxxor on 2007-10-31
I run a dual boot (XP Home and Ubuntu). 

In Gnome, the partitions are  shown as icons on the desktop. How can I remove these icons?

---

### Post by It_Was_Luck on 2007-10-31
I also do the same thing, and I also Have the icons, I haven't found a way yet, but perhaps someone else will know?

---

### Post by erginemr on 2007-10-31
Run "gconf-editor" from a terminal (It is also hidden under Main Menu -> Applications -> System Tools. You need to use the menu editor to enable it.)

Inside gconf-editor program, from Apps-> Nautilus -> Desktop, uncheck the volumes_visible option.

---

### Post by erginemr on 2007-10-31
See the attached screenshot for a better view.

---

### Post by It_Was_Luck on 2007-10-31
Worked nicely, thanks

---

### Post by erginemr on 2007-10-31
You are welcome.

Happy 'bunting...

---

### Post by vmaric on 2007-10-31
hi everyone .

I just upgraded ubuntu feasty 7.04 on version 7.10 and i have a litl problem like in 7.04
i havent sam things, like a can not see battery on gnome panel and i cant put it there.

meesage of my ubuntu is:

The panel encounterd a problem, while loading. (And when reboot it I have same things)

OAFIID:GNOME_MixerApplet_BattstatApplet

Have somebody eny idea?

I reinstall gnome-panel and gnome-panel-data and it dont help me!
:(:(
__________________

---

