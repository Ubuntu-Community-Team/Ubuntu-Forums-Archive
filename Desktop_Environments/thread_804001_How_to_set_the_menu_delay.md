---
title: "How to set the menu delay"
date: 2008-05-22
forum: Desktop Environments
---

### Post by wrgb2 on 2008-05-22
Is there a way to set the menu delay in the Gnome main menu?  By menu delay, I mean how long it takes for each menu to appear when you hover the mouse over its name.
Thanks,

---

### Post by wrgb2 on 2008-05-22
Bump.  Anybody know the answer to this one?
thanks,

---

### Post by angry_johnnie on 2008-05-23
Maybe [this]("http://ubuntuforums.org/showthread.php?t=215119") will do it.

---

### Post by wrgb2 on 2008-05-23
Thanks for the info.  That forum posts seems to be addressing the problem - I'll try it.

---

### Post by shuffman37 on 2009-08-15
"Faster Gnome/UBUNTU Menus
I’ve noticed that sub-menus tend to be a little “sticky”. It seems there is a 1/4s delay in usability. 
Click "Places", "Home Folder". Now, we need to create a file called .gtkrc-2.0. To do this we right-click on any white space and move our mouse over "Create Document" and click "Empty File". We now rename this file to .gtkrc-2.0.

We will now double-click the ".gtkrc-2.0" file you just created and add the following line to it;
gtk-menu-popup-delay=0
Click Save and close the window.  You will have to log back in to see the results.
If you feel your Ubuntu menus open too fast now and would like to make them slower, the suggested optimal speed is:
gtk-menu-popup-delay=100
However, for you to be able to edit ".gtkrc-2.0" again we need to tell Ubuntu to show hidden files.
Go back to your "Home Folder"
Click "View" and a menu expands. In this menu you will find something called "Show Hidden Files", click it.
You will now be seeing a whole bunch of files you have never seen before. Find the file called ".gtkrc-2.0", open it and delete gtk-menu-popup-delay = 0, replace it with gtk-menu-popup-delay = 100.
If for whatever reason you do not like this tweak, it is safe to delete the file called ".gtkrc-2.0" and all will be back to normal."

[http://www.goitexpert.com/general/ubuntuguide/]("http://www.goitexpert.com/general/ubuntuguide/")

---

### Post by harry2006 on 2009-08-15
try making use of search button @ top-right corner....someone might have faced the problem you're facing now...and you'll get the solution right away instead of someone making you look at those old thread or reposting the same solution...

---

