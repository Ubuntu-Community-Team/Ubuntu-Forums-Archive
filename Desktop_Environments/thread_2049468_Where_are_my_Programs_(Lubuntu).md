---
title: "Where are my Programs? (Lubuntu)"
date: 2012-08-28
forum: Desktop Environments
---

### Post by OllyRoberts on 2012-08-28
Evening All.

Im a bit of a noob. Go easy on me.

i have succesfully installed a .Jar of a program i want.
I have also installed the LXDE main menu editor, so that I can add it to my "start menu"
it opened, and ran, and was fine, once i had installed it.
but i closed it, and cannot for the life of my get it back!
where do programs go when they are installed?

i pressume its a little different for ".Jar" files, as the internets is not providing much in the way of help.

Hope you can point me in the right direction.

Ol

---

### Post by black veils on 2012-08-28
the .jar file will be in your files, accessible through the file manager, wherever you last saw it. if you want it in the menu, it needs to be manually added.

---

### Post by ajgreeny on 2012-08-28
Try the command **lxmed** in the Alt+F2 run box, then use that command (if it works for you) in the command box of a new item that you add to the menu whilst using the menu-editor.

---

### Post by Rodney9 on 2012-08-28
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_make.2BAC8-add_an_application_to_the_.22start.22_menu](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_make.2BAC8-add_an_application_to_the_.22start.22_menu).


For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by Gaygerbil on 2013-05-12
Applications in LxMenu can be found under

/home/USERNAME/.local/share/applications

and

/usr/share/applications

You can delete and add custom entries from there for future reference. They are done in .desktop format which is pretty self explanatory just open one of the desktop files in a text editor to check it out. Good luck and if you need more help don't be hesitant to ask here.

---

