---
title: "Xubutu edit right click mouse launcher"
date: 2012-12-04
forum: Desktop Environments
---

### Post by Portaro on 2012-12-04
How i can edit the menu that appear in xubuntu- when i do a right click on xubuntu workspace appear a menu with some launchers, i need know how i can edit him and where.

Thanks.:popcorn:

---

### Post by Frogs Hair on 2012-12-04
I use the XFCE 4.10 session and the settings editor has an entry for the context/xfce 4 desktop menu , but I see no way to edit it. Xubuntu may differ. You may want to check home > hidden folders .config folder.

---

### Post by Toz on 2012-12-04
The right-click context menu is hard coded and cannot be edited without altering the source code. See post #3 [here]("http://forum.xfce.org/viewtopic.php?id=7099").

However, the main menu displayed at the bottom of the right-click menu can be edited (if you've disabled icons on the desktop, you'll only see the main menu on right click). To do so, right-click the Menu panel item in the top left corner (the default location), select "Properties" and Edit Menu. Again, this will only edit the main applications menu, not the right-click context menu. 

You can however, add items to this menu by creating Thunar Custom Actions. See [here]("https://help.ubuntu.com/community/ThunarCustomActions") and [here]("http://docs.xfce.org/xfce/thunar/custom-actions").

---

