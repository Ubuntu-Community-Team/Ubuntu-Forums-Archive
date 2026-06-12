---
title: "[SOLVED] Copying K-Menu for other users"
date: 2007-08-27
forum: Desktop Environments
---

### Post by knichel on 2007-08-27
I have created the "ideal" kmenu for my setting.  I wish to make this the starting point for all new users.  What do I need to copy to /etc/skel to make this  happen?

I am using kubuntu Feisty.  Just installed all apps I wanted and am ready to create users.  Before I create users I would   like to set up /etc/skel so they don't have to recreate all menu  items again.

Thanks,
Mike

---

### Post by bmorency on 2007-08-31
the menu file you are looking for is ```
/home/user/.config/menus/applications-kmenuedit.menu
``` 

that is the file that has all the entries in the k menu.  i'm not sure how to get it in the right spot using /etc/skel, i have never used it before. 

if you look in the file there is an entry for each application you have in the menu (each entry ends with .desktop). kde looks for these .desktop files in either "/usr/share/applications/kde" or "/home/user/.local/share/applications/". so when you click a menu item it looks at this .desktop file to run the program. if you have any in the second folder i think you might have to copy them to the first folder so everyone can access them. so if you manager to copy the .menu file to the right spot everyones menu should look the same. 

hope this work for you.

---

