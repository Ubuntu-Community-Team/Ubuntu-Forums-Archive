---
title: "Custom Panel Menu"
date: 2007-05-05
forum: Desktop Environments
---

### Post by starfry on 2007-05-05
Hello,

I'd like to add some custom menus to the top panel on my desktop. 

I want to be able to create my own favourites menus for my common tasks but there seems to be no easy way to do this. 

I realise I can use the drawer but I don't like the "sticky" nature of them. I just want my own menu hierarchy (like "applications" but with my stuff in it).

Is there a way to do this?

Thanks in advance.

---

### Post by starfry on 2007-05-05
I've been able to get a menu on the bar with my own icon in it, tooltip, etc, but it just shows the same items as the main "Applications" menu. This is despite me setting the "use_menu_path" and "menu_path" to specific vaiues using the "gconf-editor" programme. No matter what I do I can't change the menu items. I know I'm editing the right item because I can change other attributes such as the icon file.

---

### Post by starfry on 2007-05-14
Hi, no replies so I guess this is just not possible then....

---

### Post by Kobalt on 2007-05-14
There are a few things you can do from using the menu editor Alacarte. Use Alt+F2, then *alacarte* to launch it.

---

### Post by starfry on 2007-05-20
Yes I've tried alacarte, but I want to start a new menu at the same level as Applications, System and Places so it appears as a 4th item on the panel itself. I don;t want a sub-menu of Applications.

---

### Post by Perfex on 2007-05-20
you need to use the panel menu type that does not have the "Applications Places System" text.

1. Right click the panel and choose "Add to Panel". 

2. Add the "Main Menu" item. You should get a panel menu that has only an icon (no text). 

3. You can remove the previous menu by right click and "Remove From Panel"

4. Open "Gnome-Panel -> System Tools -> Configuration Editor"

5. Navigate to "apps/panel/objects".

6. Find the "object_" entry where "object_type" is equal to "menu-object".

7. Check "use_custom_icon".

8. Set the value of "custom_icon" to the path of the icon. It should change as soon as you set the path.

---

### Post by starfry on 2007-05-21
Sorry, I'm probably being dumb, but I can't find "Gnome-Panel -> System Tools -> Configuration Editor".

I've right clicked in the panel, looked under Applications, Places and System and I am at a loss. Is this something that is not part of the base Ubuntu install that I need to install ?

---

### Post by adampyre on 2007-05-30
Hey,

It is hidden by default. Right click the menu, click edit menus, click system tools and check the configuration editor check box to show it.

---

### Post by starfry on 2007-08-04
Hey! I dumped this idea but had to come back to it. I've tried several times now to sort this out but it looks like it is not possible. Perhaps there is some plugin that allows you to create additional menus.

All I want is another menu name on the bar next to the existing 3 "Applications Places System" menus items (like: Applications Places System MyStuff). then to create my own menu items below MyStuff.

I don't like the drawers because you can't label the items, only have icons. 

Any ideas?

---

### Post by BetaguyGZT on 2007-08-04
XFCE will let you do this. Fully custom menus (and multiple menus) is fairly straightforward and pretty easy to do.

Here's what you do (and this is geared for people who **don't** have XFCE installed! If you already have it you can skip step #1):

**Step #1**

```
sudo apt-get install xubuntu-desktop
```

Let it go thru the motions; when it's done, log out and then back in as an XFCE Session.

**Step #2**

Right-click on your XFCE Menu, and 'Edit Menu'. The XFCE Menu Editor comes up. What you'll be doing is backing up your original menu first, so click on **File -> Save as..** and name it 'menu_orig.xml' . This is our failsafe: In case of problems or whatnot, simply rename the file back to 'menu.xml' and reload it. Use **File -> Save as...** again, but **this** time name it 'menu2.xml' instead. This will be our new custom menu file that we'll load in step #3. We don't want to overwrite the one that the first menu is using (which is menu.xml), since we still need that. For additional menus, simply repeat the process and name your menu file sequentially (menu3.xml, and so on).

**Step #3**

Right-click your XFCE Panel, add another XFCE Menu (it'll be all the way at the bottom of the list). It's properties comes up as soon as you add it. 1/3 of the way down the dialog, in 'Menu File', tick the 'Use custom menu file' and browse to 'menu2.xml'. in 'Button title' at the top, name it whatever you like. At the bottom, you can select a custom icon (or simply not use one at all, your choice). Hit 'Close', at the bottom.

**Step #4**

Edit your menus as desired. Remember to make **sure** that you aren't saving your menu.xml files as the original 'menu.xml' file! I recommend that you use 'Save as...' each time you edit, just to make sure.

Hope that helps someone -- I know it's not for Gnome, but I use a Gnomified menu layout for XFCE and it works great. :popcorn:

---

### Post by starfry on 2007-09-27
Thanks for that. I've decided to change desktops so I will take a look at XFCE.

---

### Post by starfry on 2007-10-23
Thanks for that.
I'm unclear what the difference between window managers is. Does changing between Gnome, XFCE, KDE, etc change the available applications that you can run or is it just the window manager itself that changes?

SImply put, if I change to XFCE will I still be able to use everything I use now?

I was planning to move to KDE when I do my next upgrade, which I anticipate to be 8.04.

---

