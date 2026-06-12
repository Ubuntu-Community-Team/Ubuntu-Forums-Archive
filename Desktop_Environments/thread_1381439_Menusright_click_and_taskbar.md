---
title: "Menusright click and taskbar"
date: 2010-01-14
forum: Desktop Environments
---

### Post by MiCK.ca on 2010-01-14
Ok, I did read the tutorial about right-click menu editing

[http://ubuntuforums.org/showthread.php?t=1105162](http://ubuntuforums.org/showthread.php?t=1105162)

however, this for some reason does nothing to right click menu for me. I can edit the xfce-applications.menu and choose it via the properties but it only effects the taskbar menu not the right-click menu. 

Where is the actually menu file for the right click menu. attached you'll see the task menu and the right click menus...why aren't they the same? Is this a problem with the menu editing capabilities in xfce4.6? OR is the right click a complete different file in xfce 4.6?

any help would be great...I'm stumped.

---

### Post by Brandon Williams on 2010-01-15
First, I recommend against modifying the system-level menu and desktop files. Just modify them for your user instead. It's safer, and better protected against over-writes on installation/upgrade. Instead of editing /etc/xdg/xubuntu/menus/xfce-applications.menu in place, copy it your ~/.config/menus/ directory and edit your own copy.

That's not your problem, though. Open the desktop configuration gui (the one where you select wallpaper, etc.) and click on the Icons tab. You have to set 'Icon type' to 'None' if you want just the Applications menu to appear on right-click. You either get icons on the desktop or a plain applications menu. You can't get both as far as I can tell.

---

### Post by MiCK.ca on 2010-01-15
Thank you for your polite reply...got worse in other places for the same question. Your advise is sound and I generally always backup copies to my home folder. 

Thank again for your reply.

---

