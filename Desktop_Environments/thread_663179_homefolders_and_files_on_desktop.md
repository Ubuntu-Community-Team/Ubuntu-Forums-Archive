---
title: "/home/folders and files on desktop"
date: 2008-01-09
forum: Desktop Environments
---

### Post by aldodefilippi on 2008-01-09
When I create a folder or add a file in the /home/username directory it also appears on the desktop. If I delete it ffrom the desktop it's also deleted from the  /home/username directory. How can I stop this? I just downloaded and installed the newest Ubuntu version and I probably messed up when configuring the desktop......

thanks, aldo

---

### Post by ilovebsod on 2008-01-09
hold down the alt button and press F2, it should bring up the run box.  in the run box type gconf-editor

browse down to

apps \ nautilus \ desktop

unchecking everything will give you a blank desktop, or just uncheck what you don't want to see

---

### Post by aldodefilippi on 2008-01-09
Sounded like a great idea and tried it. Restarted the computer and was told that an error occurred and that some of my configuration changes may not have "applied"....

aldo

---

### Post by ilovebsod on 2008-01-09
go back into gconf-editor and see if the boxes you unchecked are still unchecked.

---

### Post by aldodefilippi on 2008-01-09
"An error occurred while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly."

that's what I get. 


aldo

---

### Post by ilovebsod on 2008-01-09
you get that when you try to launch gconf-editor?

---

### Post by aldodefilippi on 2008-01-09
no, i get that message after i have "un-ckecked" the box you mentioned (e.g. "false") and closed the window/exited. 

aldo

---

### Post by samwyse on 2008-01-10
It's actually apps/nautilus/preferences/desktop_is_home_dir that you need to uncheck.

---

### Post by aldodefilippi on 2008-01-10
When I ask for "details" on the error message, I get this:



Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/home_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/home_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/home_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/home_icon_name
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name

---

### Post by ilovebsod on 2008-01-10
try creating a new account, go into gconf-editor and list out everything that is in the desktop

---

### Post by aldodefilippi on 2008-01-10
great! now how do i get rid of the "ERROR" messsage box which appears whenever I log in? thanks. aldo

---

### Post by funkysod on 2008-01-28
the problem is solved by changing icon theme and then if u like change it right back to your original one. saved my day.. hope this helps someone!

---

