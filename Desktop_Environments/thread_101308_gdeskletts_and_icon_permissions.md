---
title: "gdeskletts and icon permissions?"
date: 2005-12-09
forum: Desktop Environments
---

### Post by mcescher on 2005-12-09
I have a problem trying to assign icons to a launcher bar in gdesklets.

I have the launcher bar set up and have added a shortcut to a program (gnomebaker for instance).

When I try to assign an icon to the launcher I get those that are in the default directory that come up (usr/share/pixmaps) by default. I do not like any of those so I have downloaded an icon pack from gnomelook.org and extracted it into a folder in my home directory. I proceed to browse to that folder and when I get there I can see each of the .png icon files and their names but they are all greyed out and i can't select them to assign them as icons.

I have checked the permissions on the folder and subicons and i am the owner with all priveledges.

I have even tried to place one icon on the desktop and select it but it still won't let me do it.

I am just wondering why it will not let me select them....any ideas?

---

### Post by Sutekh on 2005-12-18
Its not a permissions problem.  When you change the icon and you browse to the folder that has your icon, you are actually browsing for the *folder* not the icon.

When you originally click Custom Icon it opens a dialog box with the contents of '/usr/share/pixmaps/' displayed.

Click browse and go to your icon folder and click ok, then it should go back to the first dialog box. Just press return to update the path and it should display the contents of your icon folder.

The other way is to open the launcher properties and drag the icon you want from a browser to the box that says "No Icon"

Post #4 and #12 in this thread - [Access to Icons themes]("http://www.ubuntuforums.org/showthread.php?t=89835&highlight=icons+greyed"), have nice pictures to show how to do this.

---

