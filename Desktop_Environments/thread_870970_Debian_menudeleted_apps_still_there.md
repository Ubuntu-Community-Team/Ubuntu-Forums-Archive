---
title: "Debian menu/deleted apps still there"
date: 2008-07-26
forum: Desktop Environments
---

### Post by rick71 on 2008-07-26
Can anyone tell me how to remove Debian menu items for apps that have been deleted?

Thanks.

I tried to post this earlier, but it doesn't seem to have posted. I apologize if this ends up being a duplicate.

---

### Post by RedSquirrel on 2008-07-26
Maybe you could try to regenerate the Debian menu. Run (in a terminal):

```
sudo update-menus
```

---

### Post by rick71 on 2008-07-26
update-menus didn't work. The menus entries are still there, and the apps aren't.

---

### Post by kerry_s on 2008-07-26
i'm going to assume your using gnome.

use the alacarte menu editor, click on debian on the left, uncheck what you don't want on the right, if you uncheck them all it will turn off the debian menu.

i would give exact instructions, but mines still installing i'm at 443 of 657, so i still got awhile to go. :)

okay it's applications> accessories> alacarte menu editor

---

### Post by rick71 on 2008-07-27
I am using both Gnome/Metacity and Windowmaker. 

Under Gnome, the menu item isn't listed when you cuncheck the item using the menu editor, but that doesn't really alter the menu source. Under WindowMaker, after using the Gnome menu editor, the menu items are still there.

Using the editor work sort of work under Gnome, but there are a lot of KDE entries that shouldn't be there.

Is there a way to use xdg to generate a new, correct menu?

---

### Post by kerry_s on 2008-07-27
> **rick71 said:**
> I am using both Gnome/Metacity and Windowmaker. 

Under Gnome, the menu item isn't listed when you cuncheck the item using the menu editor, but that doesn't really alter the menu source. Under WindowMaker, after using the Gnome menu editor, the menu items are still there.

Using the editor work sort of work under Gnome, but there are a lot of KDE entries that shouldn't be there.

Is there a way to use xdg to generate a new, correct menu?


that would be the "sudo update-menus" as RedSquirrel said, if your still seeing them after running that, then there most likely still installed, did you use synaptic to uninstall them completely?

---

### Post by rick71 on 2008-07-27
> **kerry_s said:**
> that would be the "sudo update-menus" as RedSquirrel said, if your still seeing them after running that, then there most likely still installed, did you use synaptic to uninstall them completely?

Yes. And as far as I can see in Synaptic, I have no KDE apps installed.

---

### Post by kerry_s on 2008-07-27
check your hidden files, see if the menu is on the user side. it's been years since i used windowmaker so i can't remember the set up.
or
try running> update-menus < with out the sudo.

other then that i'm out of ideas, sorry.

---

### Post by rick71 on 2008-07-28
> **kerry_s said:**
> check your hidden files, see if the menu is on the user side. it's been years since i used windowmaker so i can't remember the set up.
or
try running> update-menus < with out the sudo.

other then that i'm out of ideas, sorry.

Thanks. I tried udate-menus as a user. Kate and Kwrite are still in the menus in Gnome, but not Windowmaker. Strange. But, at least for now, the Windowmkare menus seems to be correct, and I can always just uncheck whatever items I don't want in Gnome.

Thanks for al the help.

---

### Post by kerry_s on 2008-07-28
> **rick71 said:**
> Thanks. I tried udate-menus as a user. Kate and Kwrite are still in the menus in Gnome, but not Windowmaker. Strange. But, at least for now, the Windowmkare menus seems to be correct, and I can always just uncheck whatever items I don't want in Gnome.

Thanks for al the help.

ahh, so that means windowmaker keeps it's menu on the user side. as long as your happy, i'm happy. :)

don't forget to mark the thread solved

---

### Post by rick71 on 2008-07-28
> **kerry_s said:**
> ahh, so that means windowmaker keeps it's menu on the user side. as long as your happy, i'm happy. :)

don't forget to mark the thread solved

I am happy enough. The solution seems workable in each situation, though I'm not sure why the differences are there. And I guess it is close enugh to mark solved :-)

Still, I wonder what will happen when I add/delete new apps...
But until then .. thanks.

---

### Post by rick71 on 2008-08-12
I have found that applications are not being added, so this is still not working properly, at least with Windomaker.

---

