---
title: "[SOLVED] Xfce task list buttons wrong size"
date: 2007-10-31
forum: Desktop Environments
---

### Post by ruru on 2007-10-31
I've just upgraded to xubuntu gutsy (amd64) and have an issue with the icons/buttons on the task list. The buttons want to be minimum 100px high and the icons appear to be 16x16. 
I have tweaked the system a bit since - but this problem was there immediately after a clean install. 
My  ~/.config/xfce4/panel/tasklist-11937513761.rc file is:
```

grouping=1
all_workspaces=1
show_label=0
expand=1
flat_buttons=0
width=100

```

Manually setting the 'width' value will be overwritten back to 100 when restarting the panel. I can't find any reference to other options to add to this file that might help...


Does anyone know how to set this up properly (icons/buttons scaled to panel width)?

---

### Post by ruru on 2007-11-03
It was Icon Box that I wanted! As far as I can see it is the same thing as Task List  with proper icons...

---

