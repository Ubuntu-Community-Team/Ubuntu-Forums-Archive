---
title: "I've deleted my top panel"
date: 2010-05-25
forum: Desktop Environments
---

### Post by DJH91 on 2010-05-25
Like an idiot ive deleted my top panel trying to fix something how to i reset it back to normal?
I also have 2 invisible panels either side of my screen, how do i get rid of them?

thanks in advance. :(

---

### Post by sidewalkcynic on 2010-05-25
Right click on one of the panels, and there should be preferences - try it.
Should be able to reset top, and remove sides.
then you will have to add all the stuf you want on the panel from the preference menu

If not open a terminal and type, gnome-panel.

---

### Post by mikewhatever on 2010-05-25
Right click the bottom panel, select 'New Panel' to re-add the top panel. As for other panels, delete the ones you don't want just as you deleted the top one.

---

### Post by ajgreeny on 2010-05-25
To go back to the default for panels on the desktop simply delete (or rename) the folder in the hidden **~/.gconf/apps/panel** in your home, then run the command ```
killall gnome-panel
``` Your current panel(s) will disappear and the two default ones should re-appear.

---

