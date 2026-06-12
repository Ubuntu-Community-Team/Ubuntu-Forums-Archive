---
title: "Edit launcher icons"
date: 2013-04-28
forum: Desktop Environments
---

### Post by johnno56 on 2013-04-28
I know how to add a shortcut / launcher to the desktop, but what I cannot figure out is, how to edit or change the shortcut's icon. With Ubuntu all I had to do was examine the "properties" of the shortcut and click the icon and change it. Lubuntu does not seem to have this function. Can someone show me how it's done?

Many thanks

J

---

### Post by Dennis N on 2013-04-28
When you say 'launcher' I assume you mean _application_ launcher. 

If you copied the .desktop file of the application to your desktop from **/usr/share/applications**, then you should be able to edit the file with a text editor and use the full path to whatever icon you want (line starting Icon= ). 

If its a symbolic link to a file, it will use the system theme's icon for a link to the particular file type on the desktop. Can't advise on changing that.

---

