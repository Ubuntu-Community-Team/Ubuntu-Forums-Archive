---
title: "application groups for gnome-panel"
date: 2012-01-09
forum: Desktop Environments
---

### Post by wujj123456 on 2012-01-09
I am using GNOME classic in 11.04. I want to group a bunch of launchers together. I expect when I click that icon, a list of icons pop-up in a menu for selecting (just as "Places" or "Applications"). It's also somehow  similar to a user-controlled jumplist.

Does anyone know how to achieve this? Since "Application" and "Place" menu resembles what I want to achieve, it should be possible, right? 

Thanks.

---

### Post by jerrrys on 2012-01-11
One possibility would be "alacarte"

---

### Post by Frogs Hair on 2012-01-11
There was an applet in the Gnome 2 add to panel menu with the ability to include a number of items . I can't remember the name though .

---

### Post by jerrrys on 2012-01-11
Drawers? Desktop Drawers?  That what your thinking of?

---

### Post by wujj123456 on 2012-01-11
> **Frogs Hair said:**
> There was an applet in the Gnome 2 add to panel menu with the ability to include a number of items . I can't remember the name though .
> **jerrrys said:**
> Drawers? Desktop Drawers?  That what your thinking of?
Wow, thanks. That's pretty close. Though I actually want the text title instead of an icon. (My applications are all command line launchers, and it would be quite painful to find a unique and meaningful icon for each of them...)

Any idea what its package name is? Or source code? Perhaps I can try hacking it.

---

### Post by Krytarik on 2012-01-11
> **wujj123456 said:**
> Any idea what its package name is? ... Perhaps I can try hacking it.
The Drawer is part of "gnome-panel"; good luck with hacking it!

Regards.

---

### Post by wujj123456 on 2012-01-11
> **Krytarik said:**
> The Drawer is part of "gnome-panel"; good luck with hacking it!

Regards.
Thanks. I've found the source. Looks like a good mini-project, but I guess I'm the very few who want ugly titles instead of shiny icons. 

For now, I used "alacarte" to put those launchers into the application menus. Just one more click and move than expected, but I can use gnome-do to launch them too. (Why haven't I thought of this simple idea before...)

---

### Post by Krytarik on 2012-01-11
> **wujj123456 said:**
> ... but I guess I'm the very few who want ugly titles instead of shiny icons. ...
Nah, it makes totally sense, particularly as a matter of consistency towards the other, default menus. [-X (not the 'shame on you' part)

But I'm glad you found your way around of hacking it for now. :-)

---

### Post by mcduck on 2012-01-12
> **wujj123456 said:**
> Thanks. I've found the source. Looks like a good mini-project, but I guess I'm the very few who want ugly titles instead of shiny icons. 

For now, I used "alacarte" to put those launchers into the application menus. Just one more click and move than expected, but I can use gnome-do to launch them too. (Why haven't I thought of this simple idea before...)

You can drag&drop any existing menu category (or one that you've created yourself) from the menu into the panel. (it will appear as icon in the panel, but when you open it you should get a normal text menu instead of icon list like with drawers).

---

### Post by jerrrys on 2012-01-12
> **mcduck said:**
> You can drag&drop any existing menu category (or one that you've created yourself) from the menu into the panel. (it will appear as icon in the panel, but when you open it you should get a normal text menu instead of icon list like with drawers).

Wished that would work in gnome3 :(

---

### Post by Krytarik on 2012-01-13
> **mcduck said:**
> You can drag&drop any existing menu category (or one that you've created yourself) from the menu into the panel. (it will appear as icon in the panel, but when you open it you should get a normal text menu instead of icon list like with drawers).
Ok, now that the OP apparently doesn't do that, I myself have got to ask: I've tried that yesterday with every current version of Ubuntu, that is, Lucid 10.04, Natty 11.04, and Oneiric 11.10, and it just doesn't work that way. So how did you come to that, and if not a mistake, how does one get it to work that way? :-k :P

---

### Post by mcduck on 2012-01-13
> **Krytarik said:**
> Ok, now that the OP apparently doesn't do that, I myself have got to ask: I've tried that yesterday with every current version of Ubuntu, that is, Lucid 10.04, Natty 11.04, and Oneiric 11.10, and it just doesn't work that way. So how did you come to that, and if not a mistake, how does one get it to work that way? :-k :P

That should work if you are running Gnome 2 desktop, with Gnome-panel.

I rember that you can add the menu categories, in addition to just menu items, into the panel straight from the Applications menu. But it's been a while since I've had Gnome 2 on any of my computers, so I can't check the exact way. But if dragging from menu to panel doesn't work, try right-clicking one of the menu categories.

---

### Post by Krytarik on 2012-01-13
> **mcduck said:**
> That should work if you are running Gnome 2 desktop, with Gnome-panel.

I rember that you can add the menu categories, in addition to just menu items, into the panel straight from the Applications menu. ... But if dragging from menu to panel doesn't work, try right-clicking one of the menu categories.
Nope, still doesn't work, neither dragging, nor does a right-click on the categories bring up anything. Anyway. :-)

---

### Post by mcduck on 2012-01-14
All right, I just downloaded 10.04 LTS again, just to try this, and it *does* work (even though I rembered the exact method slightly wrong ;))

You can't drag the submenu itself, or right-click it. However if you right-click any item inside a submenu, you get an option to add the entire submenu to your panel, as a drawer or as a menu.

For example, Go to Applications->Internet, right-click the Firefox entry and choose Entire Menu->Add This as Menu to Panel.

---

### Post by Krytarik on 2012-01-14
> **mcduck said:**
> You can't drag the submenu itself, or right-click it. However if you right-click any item inside a submenu, you get an option to add the entire submenu to your panel, as a drawer or as a menu.

For example, Go to Applications->Internet, right-click the Firefox entry and choose Entire Menu->Add This as Menu to Panel.
Yay, this way it works here, too! \\:D/
Quite nice that feature, eventually! :D

Now that you've mentioned it, I remember having seen that "Entire menu" sub-menu before, and having found that not exactly senseful already back then, and now that we've actually needed those options, it wasn't really obvious to search them in the context menu of the launcher items. :P

So sorry for making you download the Lucid 10.04 ISO, but hey, it's an LTS version, so you might re-use it at a later point. ;-)

---

### Post by Krytarik on 2012-01-22
As a follow-up, this method works in both Gnome 2 and Gnome 3 Fallback, to add additional menus (also custom ones) to the Gnome Panel, as discussed before:
> **linfidel said:**
> By the way, I've discovered a trick if you want to add new menus to the the panel. I'm doing this in 11.10 gnome classic desktop, but it may work in gnome 2.

First, create a new custom menu using alacarte, with possibly at least one item; or you can skip this and add a whole existing menu, if desired. If you will want a custom icon for the menu on the panel, pick an icon now by clicking on the icon.

**Then, from the "add to panel" menu, choose "Application Launcher", then the Forward button; now, choose the menu you want to add, and press the "add" button. The new menu should show up on the panel, and you can edit it using alacarte. This menu can be hierarchical, if so desired.**

---

### Post by wujj123456 on 2012-01-22
> **Krytarik said:**
> As a follow-up, this method works in both Gnome 2 and Gnome 3 Fallback, to add additional menus (also custom ones) to the Gnome Panel, as discussed before:
Wow, thanks for the follow up. Now I can launch them whichever way I want. :P

---

