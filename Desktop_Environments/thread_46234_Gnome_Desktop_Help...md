---
title: "Gnome Desktop Help.."
date: 2005-07-03
forum: Desktop Environments
---

### Post by cyanideoverdose on 2005-07-03
Ok.. My compturer boots up fine.. everything goes as planned but.... 
My desktop wallpaper nor my icons come up, only after I go to >places>Home Folder
then my desktop icons and my wallpaper show up.. I've waited for like an hour and it doesnt show up until I do that.. 
Im using hoary and i have firestarter and gdesklets set to start up, and they both start up, no problem.. any ideas why my desktop and icons dont show up?

---

### Post by varunus on 2005-07-03
This means, for some reason, that nautilus is not starting automatically for some reason.  Nautilus provides the desktop along with the file browser (which is why opening your home folder makes the desktop icons appear).  A workaround would be to go to system-preferences-sessions, click on the startup programs tab, and add "nautilus" to the list (the order doesn't matter).  I'm not sure of the cause of the problem...maybe reinstall the nautilus or gnome-session packages through synaptic?

---

### Post by cyanideoverdose on 2005-07-04
Thanks.. re-installed nautilus through synaptic, and now it seems to work right..

---

