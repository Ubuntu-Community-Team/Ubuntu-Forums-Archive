---
title: "Backup Gnome Menu Launchers"
date: 2009-03-18
forum: Desktop Environments
---

### Post by RealG187 on 2009-03-18
[http://ubuntuforums.org/showthread.php?t=531216](http://ubuntuforums.org/showthread.php?t=531216)

I want to know this too.

I want to save my Gnome Menu setup so I don't have to reconfigure it, is there a folder I can backup and restore to backup and restore my menu? I am sure there is a .something folder inside the home folder responsible for storing the menu config...

---

### Post by manuelb on 2009-05-05
I second that, my **~/.config/menus/applications.menu** configuration looks like default settings or something like that.

---

### Post by wirespot on 2010-07-12
The menu definitions are kept in these dirs:

```
~/.config/menus/
~/.local/share/applications/
~/.local/share/desktop-directories/
```

Usually the customizations are placed in files starting with **alacarte-*** so you can try restoring just those for starters and see if it's enough.

You will most likely have to logout and relogin to see the changes, or you can `killall gnome-panel` in the console.

---

