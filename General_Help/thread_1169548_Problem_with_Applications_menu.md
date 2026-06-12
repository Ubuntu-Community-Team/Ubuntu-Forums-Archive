---
title: "Problem with Applications menu"
date: 2009-05-25
forum: General Help
---

### Post by LKnives88 on 2009-05-25
Alright, first off I am running Ubuntu 8.04.

I had the Main Menu application crash earlier today and, after a restart of my machine, have lost the Applications drop down menu.  Places and System still work just fine and the Main Menu application has gone from crashing when I try to remove something to just crashing when I try to open it.

Any ways of rebuilding the program and restoring the menu without having to using the original CD?  Not sure if my 2 builds old CD would work.

---

### Post by Wobblybob on 2009-05-25
Hi, assuming you are using the gnome desktop,

Right click on the top panel and select [Add to Panel] scroll down the list to [Menu Bar - a custom menu bar] and drag and drop onto the top panel, this will give you Apps, Places & System.

enjoy!

---

### Post by LKnives88 on 2009-05-25
This method created a secondary Applications, Places, and System bar that has the same problem of the Applications menu not dropping down on clicking it.

Edit:  Oh, sorry.  Wasn't clear on that in the first post.  I have the menus for the 3 but Applications refuses to drop down.

---

### Post by CatKiller on 2009-05-25
```
mv ~/.config/menus /~/config/menus.backup
```

might work.

---

### Post by LKnives88 on 2009-05-25
> **CatKiller said:**
> ```
mv ~/.config/menus /~/config/menus.backup
```might work.

No such file or directory.

---

### Post by _Purple_ on 2009-05-25
If you want to use mv, you have to create the directory first using mkdir as menus is a directory and there should be a dot before config.

---

### Post by LKnives88 on 2009-05-25
ect/xdg/menus had a applications.menu file that appears to be working right as a stand in.  Thanks for the help.

---

### Post by CatKiller on 2009-05-25
> **LKnives88 said:**
> No such file or directory.

You're quite right. It should have been

```
mv ~/.config/menus ~/.config/menus.backup
```to remove the old menu and generate one from the default. Just a silly typo.

---

