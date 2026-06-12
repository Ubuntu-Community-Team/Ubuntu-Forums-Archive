---
title: "[SOLVED] LXLauncher"
date: 2008-11-29
forum: Desktop Environments
---

### Post by siddartha on 2008-11-29
How can you configure this launcher? From the visual things like the display font to changing the tabs and the tab contents? On the home site there's no refference at all. Also in the provided README you have only the explanation that is the EeePC launcher replacement.

---

### Post by kerry_s on 2008-11-29
look in /usr/share/lxlauncher
you'll find a gtkrc where you can change the tab/bar colors/font.
i had no luck with changing the background.

applications are done by /usr/share/applications, there simple program.desktop launchers you just need to put it in the right category.

now when i was using gnome it would not let me edit those files, so the best way to see them is from terminal.

cd /usr/share/applications
ls
sudo gedit a-couple-of-letters-for-the-1-you-want-to-edit/look <tab>

what i do is open one close to what i want, click save as my-program.desktop then go in there and change it.

---

