---
title: "Where is &quot;Control Center&quot; or &quot;Screen Resolution&quot; in the menus?"
date: 2009-03-06
forum: General Help
---

### Post by John Wiersba on 2009-03-06
I see a number of people mentioning System->Preferences->Screen Resolution, but I don't see it in my menus.  I don't see the Control Center, either.  I can't see how to add them to the menus.

I found that I can run gnome-control-center from the command line, but I would think that it would also be accessible from a menu somewhere.  But I can't figure out how to add it.

I'm running 8.10 Intrepid Ubuntu.

Any suggestions?

---

### Post by mcduck on 2009-03-06
Since Gnome-control-center only gives a different way to access the same configurations that are in the menu by default, Linux distributions don't usualy enable both direct access to configuration tools and the control center. You can use the menu editor to enable/disable it or any other items in the menu. Just right-click on the menu and select "Edit menus".

---

### Post by beno1990 on 2009-03-06
For that you need to go to System -> Preferences -> Main menu.

Then you might see it under the preferences menu in there, but unticked.

If it's unticked you just need to tick it and you should be able to find it in the menu from now on.

If it's not there at all, just choose new item (not new menu, that does something different altogether) and put the command you use to open it on the terminal under command, and name it whatever you like. Comment you can leave blank, but it's just the little description that comes up when you leave the cursor over it for a couple of seconds on the menu.

---

### Post by John Wiersba on 2009-03-06
Both these methods worked -- thanks!  I can see both the Screen Resolution and Control Center apps now in the Gnome menu.

---

