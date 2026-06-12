---
title: "How do I regenerate the gnome-menu from installed applications?"
date: 2009-12-01
forum: Desktop Environments
---

### Post by Dthdealer on 2009-12-01
At one point my menu system went kaput - where some applications were missing from it and nearly every gui app on the system was put in the 'other' menu. 

Is it possible to remove my current menu configuration and/or restore it to what it should be?

Thanks in advance

---

### Post by Dthdealer on 2009-12-02
*bump*

---

### Post by mister_p_1998 on 2009-12-03
Right button on Taskbar, Add to Panel, Select ' Application Launcher'

Steve

---

### Post by RiceMonster on 2009-12-03
The menu reads .desktop files, so there's no real configuration.

Check to see if there's anything in ~/.local/share/applications/ and if there is, move them to another directory and see if everything goes back to default.

---

### Post by Dthdealer on 2009-12-04
> **mister_p_1998 said:**
> Right button on Taskbar, Add to Panel, Select ' Application Launcher'

Steve

You misunderstood my question.  The button/menu is not missing from my gnome-bar.

> **RiceMonster said:**
> The menu reads .desktop files, so there's no real configuration.

Check to see if there's anything in ~/.local/share/applications/ and if there is, move them to another directory and see if everything goes back to default.

Thankyou! This fixed my problem. :popcorn:

---

### Post by carlosgs on 2010-02-07
> **RiceMonster said:**
> The menu reads .desktop files, so there's no real configuration.

Check to see if there's anything in ~/.local/share/applications/ and if there is, move them to another directory and see if everything goes back to default.

Yeah! that worked!

Thanks a lot! :-)

---

