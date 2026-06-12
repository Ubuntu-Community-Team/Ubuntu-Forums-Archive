---
title: "After upgrade, menu items missing"
date: 2008-09-15
forum: Desktop Environments
---

### Post by mindless1973 on 2008-09-15
Hi,

I did an upgrade from Gutsy to Hardy recently. Everything seems to work fine with the exception that almost all of my menu items in the "Application" GNOME drop down menu are missing.

When I try to recreate the menu items by using the "Main Menu" Tool out of System - Preferences, I can't. Whenever I create a new menu item and press OK the menu item does not show up. 

There is also no error message or some other hint where I would know where to search further...

After some research, I found out that all the GNOME files do exist and are in the right directories:

/etc/xdg/menus/applications.menu

/usr/share/desktop-directories

and 

/usr/share/applications

seem to be all ok.

So, why doesn't GNOME show them in the menu bar?

any help highly appreciated!!!

bye
me.

---

### Post by I_have_seen_the_light on 2008-09-15
have you tried using the update menu command?

sudo update-menus

here is a page where you could read about it.  its for debian but since Ubuntu is based on debian it should work.  :)

[http://www.handhelds.org/~nelson/menu/ch1.html](http://www.handhelds.org/~nelson/menu/ch1.html)

---

### Post by TitanX13 on 2008-09-16
i have had the same problem. i tried yours solution and i didn't work for me

---

### Post by mindless1973 on 2008-09-16
> **TitanX13 said:**
> i have had the same problem. i tried yours solution and i didn't work for me

I don't even know where I could get this tool from. update-menus is not installed on my system :-(

bye
me.

---

### Post by TitanX13 on 2008-09-16
i tried it the first time and it ran, but then i tried to repeat it when it didn't work the first time and it tells me their is no such cmd

---

### Post by Brandel Valico on 2008-09-16
[http://ubuntuforums.org/showthread.php?t=554585&page=3]("http://ubuntuforums.org/showthread.php?t=554585&page=3")

The above link should help

---

### Post by mindless1973 on 2008-09-16
Hi,

Thanks, this article led me to the source of the problem. My /etc/xdg/menus/applications.menu file was somehow broken. After replacing it by an (older) copy it worked!

Thanks,

bye
me.

---

### Post by TitanX13 on 2008-09-16
thank you, the solution on the top of the 4th page fixed my problem. 

thanks

---

