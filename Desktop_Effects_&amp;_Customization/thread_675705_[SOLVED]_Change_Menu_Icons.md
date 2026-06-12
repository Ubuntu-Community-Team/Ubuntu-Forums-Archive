---
title: "[SOLVED] Change Menu Icons"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by halw on 2008-01-23
Running Dapper Ubuntu on a legacy laptop and want to change an icon in one of the menus. Specifically, installed Frostwire and icon in the menu is not that of Frostwire but a simple crt icon.

I would like to switch to the icon for Frostwire but, unlike kde, when I right click on the Frostwire there is no Properties selection.

Is there a way to modify the menu entry's properties to swap icons?

---

### Post by erginemr on 2008-01-23
Well, that one is easy (if Dapper Drake works the same way as Edgy, Feisty and Gutsy does, that is):

With reference to the attached screenshots, you right-click the main menu, select "Edit Menus", which brings up the "Alacarte Menu Editor", find your app, right-click, select properties, click on its icon, select a new icon from the dialog, or browse through your file system to find the correct icon for Frostwire. Possible candidates for the icon location are:
```
/use/share/icons
/usr/share/pixmaps
```
the own directory of the program, which should be something like:
```
/usr/share/frostwire
/usr/local/share/frostwire
```

The following command from the console will give you a list of all frostwire related files in your system:
```
whereis frostwire
```

---

### Post by halw on 2008-01-23
erginemr, thanks for the help. I had gone to the menu editor before and saw the correct icon there. But showed a different one when I brought up that particular entry. Didn't realize I had to go through the 'menu edit' exercise regardless.

---

### Post by erginemr on 2008-01-23
Okey dokey. Take care...

---

