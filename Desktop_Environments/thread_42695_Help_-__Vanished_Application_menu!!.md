---
title: "Help -  Vanished Application menu!!"
date: 2005-06-19
forum: Desktop Environments
---

### Post by super on 2005-06-19
I installed smeg (the menu editor) as per the instructions in the ubuntu starter guide.

fine.

then i used smeg to change the icon in the menu for firefox. saved and exited smeg. restarted gnome and now all i have is the run command on the Application menu.  :smile: 

checked smeg and it showed all the entries as being on the menu.

so is there a backup copy of the menu? what is the name of the file? is there any way to get my menu back?

thanks!

---

### Post by xristos on 2005-06-19
I don't know if it helps but you can try it :

```
killall gnome-panel
```

---

### Post by super on 2005-06-20
nope, that didn't work either.

and i just discovered that the menu of applications that is supposed to come up when you select "open with other application" in nautilus is empty as well. i think that both problems are connected.
 :-?

---

### Post by miscz on 2005-06-20
Try deleting ~/.config/menus/*

---

