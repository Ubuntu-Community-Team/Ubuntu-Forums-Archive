---
title: "Copying desktop icon to menu"
date: 2009-04-12
forum: Desktop Environments
---

### Post by brunogirin on 2009-04-12
Google Gears and Java Webstart create launcher icons on your desktop for each new application that you install that uses those technologies. I would like to move those icons to a sub-menu of the Applications menu but can't find an easy way to do it short of opening the preference window for the icon and copying everything in a new launcher. Furthermore, it looks like desktop icons can use any type of image as an icon but menu items have to use SVG.

Is there a quick and easy way to move a desktop icon to a menu? I know you can do the opposite by just dragging an item from the menu to the desktop but it doesn't work from the desktop to the menu.

---

### Post by RuleMaker on 2009-04-12
Right click on the menu -> Edit Menus pick the category where you want to add your link and select New Item.

---

### Post by brunogirin on 2009-04-13
> **RuleMaker said:**
> Right click on the menu -> Edit Menus pick the category where you want to add your link and select New Item.

Thanks RuleMaker but what I'm trying to do goes one step further than just creating a new menu entry. I would like to copy a desktop icon that was added by an application such as Java Webstart to the menu in a simple way. At the moment, this is what I do:
- right click on the desktop icon, select "properties"
- right click on the menu -> Edit Menu, pick the category, select New Item
- copy all attributes from the properties window of the desktop icon to the new item window of the menu (and then there's the problem that more often than not the icon on the desktop is not SVG so can't be used in the menu)

Is there an easier way to do this? Ideally, I would like something along the lines of: right click on the desktop icon and select something like "copy to menu"; or drag and drop from the desktop to the menu (note: the other way round works).

---

### Post by RuleMaker on 2009-04-13
I wrote a nautilus script for this (see the attachment).

Extract this to ~/.gnome2/nautilus-scripts
And next time you click on a desktop link you will see the submenu "Scripts" and click "Add to menu".
It should automatically add the icon to the menu.

P.S.
Your new icon should appear in "Other" category.

---

### Post by brunogirin on 2009-04-13
Thanks RuleMaker, it works perfectly! And it gives me a great simple example of how to do Nautilus scripts :-)

---

### Post by RuleMaker on 2009-04-13
I'm glad you liked it :)
And it's my first nautilus script.

---

### Post by brunogirin on 2009-04-14
I updated your script to handle more than one selected file and check that they were desktop entry ones. See the attachment. Note that it now only makes sense with a Gnome desktop as it uses Zenity. I'm not sure how to handle file names with spaces in them though, as the $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS variable is a space separated list of paths. Maybe split on a space followed by a / as all paths are absolute so should start with a /? But then that's stretching the abilities of bash so would probably be easier to do in perl.

---

### Post by RuleMaker on 2009-04-14
I got served :D
JK great job, tomorrow I will take a look of it.

---

