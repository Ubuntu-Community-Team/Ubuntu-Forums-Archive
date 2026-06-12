---
title: "how to reset main menu bar to initial state?"
date: 2011-03-29
forum: Desktop Environments
---

### Post by sneakyimp on 2011-03-29
Somehow my restart/shutdown button is gone from the top right hand side of my main menu in Ubuntu.  I've managed to get a shutdown button back on the menu by right-clicking it and selecting "Add to Panel..." but I really want the original button back in there.  I'm not sure what caused it to disappear but I think it was the updates that ran yesterday.

Is there anway to restore my main menu to its original, pristine state?  If so, that would rule.

---

### Post by Rubi1200 on 2011-03-29
This will restore the panels and menu to their default state. However, be warned that any custom settings you had will be **lost**. The panels will be as they were when you first installed.

In a terminal:

```
gconftool-2 --shutdown 
rm -rf ~/.gconf/apps/panel 
pkill gnome-panel
```
Log out and back in again.

---

### Post by Megaptera on 2011-03-29
For the future you might find this useful:
"PanelRestore, allows you to quickly and easily restore the default Gnome panels in Ubuntu and to backup and restore your existing custom panel configurations."

[http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/](http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/)

---

