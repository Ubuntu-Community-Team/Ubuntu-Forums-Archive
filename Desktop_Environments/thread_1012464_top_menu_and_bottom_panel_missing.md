---
title: "top menu and bottom panel missing"
date: 2008-12-15
forum: Desktop Environments
---

### Post by iranthavan on 2008-12-15
i dont know what i removed i end without top menu (application, places, system) missing like show in the laptop. 

what mistake i have made here i am sure i was cleaning up unwanted softwares and end up with this :(

pls give me some solution googled around couldnt find anything related to it or i am googling for wrong term not sure.

---

### Post by RedSingularity on 2008-12-15
Open the terminal by pressing Alt+F2 and typing "gnome-terminal" in the run box.  Then in terminal try typing this "killall gnome-panel".  That should bring it back.

---

### Post by iranthavan on 2008-12-16
but the problem is none of the function keys also working (first to put ubuntu in that state?)nor even the shortcut launcher is working.

---

### Post by maraja on 2008-12-16
same problem here after having installed cairo-dock
sometimes the top panel appears after several minutes

---

### Post by lordbux on 2009-08-31
> **maraja said:**
> same problem here after having installed cairo-dock
sometimes the top panel appears after several minutes



it seems you have uninstalled the ..tools required for all those stuff
you will have to install it.

try opening terminal like this:::
[B]==> try doing it by right clicking on desktop and selecting *create launcher*  
 
set

Type: application
name: Terminal
Comand:gnome-terminal

click ok.. now double click on the icon to open terminal <====[/B]

if you cant 
restart and enter the recovery mode.

then enter the following command:
```
sudo apt-get install gnome-panel compiz nautilus 
``` 

then restart.

if that does not help ...pls let me know which programs you deleted

---

