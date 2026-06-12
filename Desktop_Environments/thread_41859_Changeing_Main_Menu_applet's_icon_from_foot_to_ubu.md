---
title: "Changeing Main Menu applet's icon from foot to ubuntu"
date: 2005-06-15
forum: Desktop Environments
---

### Post by tristan on 2005-06-15
I'd prefer to use the Main Menu applet in place of the Ubuntu Menu Bar, in order to save a bit of gnome panel real estate. By default the Main Menu shows up with the gnome foot icon, and I'd prefer to change it to the nice ubuntu icon. However for the life of me I can't find which icon the applet uses, nor a configuration file. I'm sure the icon isn't hard coded into the applet.

Can anyone help? Thanks in advance if so...

---

### Post by tread on 2005-06-15
Got this from a Redhat forum:

gconftool-2 --set /apps/panel/profiles/default/objects/main_menu/custom-icon -t bool true

gconftool-2 --type string --set /apps/panel/profiles/default/objects/main_menu/custom-icon-file /usr/share/pixmaps/icon-you-want.png 

killall -9 gnome-panel

---

### Post by tristan on 2005-06-15
Thanks a lot for your help Tread. Unfortunately it didn't work... 

I did notice having a look at the keys in gconfeditor that they have no matching schemas, if that is important.

---

### Post by tread on 2005-06-16
Try replacing (make a backup first!) 
/usr/share/pixmaps/gnome-logo-icon-transparent.png

You will have to sudo to replace it though. If that doesnt work try gnome-logo-icon.png

And with that I am out of ideas :)

---

### Post by tristan on 2005-06-16
Tread, these were the 1st things I tried - no joy :(.

I appreciate your help.

---

### Post by dream.x on 2005-06-16
If you want to change the MAIN-MENU icon, use **gconf**, go to
**apps** > **panel** > **objects** 
and find the object with **object_type** : **menu-object**, select **use_custom_icon** and insert in the **custom_icon** field the position/name of your icon.

If you want to change the MENU-BAR icon, replace **gnome-logo-icon-transparent.png** as **tread** said and then do the **killall -9 gnome-panel** thing in terminal.

These should work.

---

