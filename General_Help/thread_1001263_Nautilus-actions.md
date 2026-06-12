---
title: "Nautilus-actions"
date: 2008-12-03
forum: General Help
---

### Post by sambita on 2008-12-03
Hello there, 

heres the thing, i have a script that i use to unmount my wd passport external hd(the reason i use a script for doing this is irrelevant) and i want to be able to have an item in the right click menu to run this script. I know that theres a scripts tree in the right click menu, thats what i've been using, but i thought it would be cool to do it this other way. 

I tried to do this by using nautilus-actions, but the menu items that i can configure there are for files or folders, and im not sure how to do this with an external hd.

Can anyone point me in the right direction?


Hope i explained myself clearly
Thanks in advance.

---

### Post by kaibob on 2008-12-03
It's not clear to me when you want the script to appear in the right-click menu. You can get it to appear when you right-click on the desktop by following the procedure outlined in the following:

[http://ubuntuforums.org/showthread.php?t=875262](http://ubuntuforums.org/showthread.php?t=875262)

---

### Post by sambita on 2008-12-04
Thanks for that, i did get it working, however what i want is for the action to be integrated with nautilus menu, instead of having a different menu on my desktop(which is what happens with compiz-deskmenu)

> It's not clear to me when you want the script to appear in the right-click menu.

If possible i want it to be context sensible, that is, i want it to show up when i right click on the My Passport icon that appears on my desktop. But from what i've been reading i dont think thats possible, so if it just shows up anytime i right-click i wouldnt mind.

Sorry if im not clear and thanks for helping me.

---

### Post by detroit/zero on 2008-12-04
Place the script in *~/.gnome2/nautilus-scripts*. It'll be there whenever you right-click.

---

### Post by sambita on 2008-12-04
> **detroit/zero said:**
> Place the script in *~/.gnome2/nautilus-scripts*. It'll be there whenever you right-click.

Thanks detroit/zero, but i have been doing that for a while, what i wanted was to show in the right click menu but not having to go to the scripts sub-menu. 

Its not that i mind doing so, its just that i want to learn to customize things like this.

---

### Post by sambita on 2008-12-04
Heres a mock up of what i want to be able to do:
[[IMG]http://img266.imageshack.us/img266/4796/passportvz6.th.png[/IMG]](http://img266.imageshack.us/my.php?image=passportvz6.png)

---

