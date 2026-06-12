---
title: "How can I group all menus into just one?"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Zonkle on 2006-01-11
Hello,

How can I group the menus "Applications", "Places", and "System" into just one menu ??
I would like to do that so I can have more space in the Tool bar.

Thanks.

---

### Post by mcduck on 2006-01-11
right-click on the paneland  select 'add to panel'. There are two different menu items, menu bar is the one with 3 separate menus, and the other one (I don't remember the name) combines all 3 to one menu button. Then remove the old menu (right-click and select 'remove from panel') and drag the new one where you want it.

---

### Post by Zonkle on 2006-01-11
This was very usefull :D Thank you very much mcduck, It worked :)

Any chance that I can edit it's icon ??

---

### Post by Thirsteh on 2006-01-11
I'm pretty confident that you'd have to replace the respective icon file on the harddrive to do that, well of course you could edit the source and recompile it, but..

---

### Post by justaguynpc on 2006-01-11
Icon replacement for main menu is pretty simple, I changed my menu setup after reading your post.

1. Right click on Main Menu icon
2. Edit Menu via Menu Editor
3. Highlight Applications ----> New Menu
4. Click the Main Menu icon to change!

'Nuf said?  

justaguy

---

### Post by Zonkle on 2006-01-11
justaguynpc it didn't work!

---

### Post by mcduck on 2006-01-11
You can change the icon with Configuration Editor. Open it (in Applications/System Tools/Configuration Editor) and browse to apps/panel/objects. Now you need to find the menu object, it's the one that has 'menu-object' as object_type. When you find it, select 'use_custom_icon' and then write path to your icon in the 'custom_icon' field.

---

### Post by ardchoille on 2006-01-12
To change the icon used in the main menu and menu bar:

```

sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png-origin

sudo cp /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```


log out and back in or

```
killall gnome-panel
```

---

### Post by justaguynpc on 2006-01-12
[QUOTE=justaguynpc]Icon replacement for main menu is pretty simple, I changed my menu setup after reading your post.

1. Right click on Main Menu icon
2. Edit Menu via Menu Editor
3. Highlight Applications ----> New Menu
4. Click the Main Menu icon to change!

'Nuf said?  

justaguy[/QUOTE]

This process allowed me not to actually change the icon because I had the gnome foot already "enabled".  However the look of the icon in this menu did offer me the option of changing it by clicking the icon itself and opening up the /usr/share/icons folder.

---

