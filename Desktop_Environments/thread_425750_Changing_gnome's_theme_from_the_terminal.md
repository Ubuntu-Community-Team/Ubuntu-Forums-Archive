---
title: "Changing gnome's theme from the terminal"
date: 2007-04-27
forum: Desktop Environments
---

### Post by mdmunoz on 2007-04-27
Context: I'm trying to get Gnome themes to apply to x** applications without actually running gnome (or popping up settings windows). So far, the closest I've come is determining that launching gnome-themes (by itself) will apply whatever theme I was using in Gnome to the x** applications.

Is there any way to apply a gnome theme without showing any gui (i.e. what is gnome-themes doing when it starts up and how can I emulate that through a terminal command, etc. without launching the gnome-themes gui)?

---

### Post by tippit78 on 2007-04-30
sudo apt-get install gtk-theme-switch

Then run 'switch' for gtk and 'switch2' for gtk2 apps. It also lets you set the font and preview your changes. Much easier and nicer than messing with gnome-theme.

---

### Post by mdmunoz on 2007-04-30
> **tippit78 said:**
> sudo apt-get install gtk-theme-switch

Then run 'switch' for gtk and 'switch2' for gtk2 apps. It also lets you set the font and preview your changes. Much easier and nicer than messing with gnome-theme.Thanks, that looks like just the thing.

(Though on my computer, it's "sudo port install gtk-theme-switch." Muahahaha...)

---

### Post by tippit78 on 2007-05-01
Warning: If you bounce back into gnome, it will create some sort of conflict with the gnome theme manager. I don't understand what the conflict is, exactly, but deleting the .gtkrc files in my home folder nicely cleans the slate.

I pop back into gnome to impress friends: Look, beryl! Nice fonts! Cool themes! Etc!

Then when they leave the room I go back windowmaker. Dull as hell, but oh god so clean and functional. Especially when you've got no RAM to speak of.

---

