---
title: "Installing Java programs for beginners?"
date: 2009-05-28
forum: General Help
---

### Post by justcop on 2009-05-28
I have downloaded a java program, unzipped it and am able to run it from the .jar file.

As a linuix newbie I am a little confused. Where am I supposed to put the folder containing the .jar file ie the equivalent of program files on windows.

Also when I have placed it in the right place how do I make it easy to launch without going to the program location. Unlike programs installed through apt-get there is no command associated with it and it does not appear in applications.

I have managed to create a link to it which I can place in the panel at the top or the desktop etc. Is this the correct way to do it. The problem with this method is that the link has rather a generic icon, how do I change the icon?

So to summarise

1)Where do I put .jar files
2)How do I add to the applications bar
3)How do I change the icon

---

### Post by pastalavista on 2009-05-28
You should put the file somewhere you won't have permissions problems like /usr/share. To make a launcher, right-click the desktop and select "create launcher" Name it whatever and the command is the full path to the file. To add it to the menu, right-click the menu bar icon and selec "Edit Menu". Add the same info in the category by clicking "Add Item". Click on the icon to change it.

---

### Post by binbash on 2009-05-28
alt + f2 then write alacarte, hit enter

Now find a good place for your launcher.When you find it, click new item and adda new item.

Write its name, browse for an icon etc.At command section,  you will write something like this (/home/USERNAME/blabla/blabla = the directory which the jar file is in)

java -jar /home/USERNAME/blabla/blabla/asdasd.jar

---

