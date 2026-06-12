---
title: "file menu gone"
date: 2008-12-05
forum: General Help
---

### Post by adamant715 on 2008-12-05
The menu which shows like file,edit,view and other types like that are gone from all my programs, so i cant do alot of things..

I attached a screenshot of what I mean.

---

### Post by Giant Speck on 2008-12-06
> **adamant715 said:**
> The menu which shows like file,edit,view and other types like that are gone from all my programs, so i cant do alot of things..

I attached a screenshot of what I mean.

Do you have global menu installed but are not using it?  You can check to see if global menu is installed by right clicking on one of the panels and clicking "add to panel."  It should be in the list as "Global Menu Applet" or something like that.

If you do indeed have it installed, open a terminal and type in the following:

```
cd
sudo gedit .gnomerc
```

It should open a blank file.  Paste the following into it:

```
export GTK_MENUBAR_NO_MAC=1 
```

Save it.  And then log out and back in.  It should be fixed.

---

