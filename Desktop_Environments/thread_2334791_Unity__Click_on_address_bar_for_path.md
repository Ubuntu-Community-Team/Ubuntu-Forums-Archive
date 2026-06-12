---
title: "Unity : Click on address bar for path"
date: 2016-08-22
forum: Desktop Environments
---

### Post by meetdilip on 2016-08-22
This is one feature I loved a lot in Cinnamon. You can click on address bar ( actually, a button beside it ) and then the address bar turns to text from blocks. You can now copy the path to current folder from there as we copy a domain name in browser. Any chance to get that in Unity ?

---

### Post by mc4man on 2016-08-22
Nothing to go with unity, it's a function of the file manager, by default that's nautilus.
Nautilus doesn't have a button for this, there is a binding to go from breadcrumbs to location - ctrl+l
(- note that there is no toggle, once in location that current window stays in location until closed. One could likely create a toggle binding using gsettings instead of the included ctrl+l

---

### Post by coffeecat on 2016-08-22
> **mc4man said:**
> 
(- note that there is no toggle, once in location that current window stays in location until closed. One could likely create a toggle binding using gsettings instead of the included ctrl+l

No need to create a binding. There is already a toggle in Nautilus to go from location to breadcrumbs - esc.

---

### Post by mc4man on 2016-08-22
> **coffeecat said:**
> No need to create a binding. There is already a toggle in Nautilus to go from location to breadcrumbs - esc.
Cool, I tried alot of keys, didn't think to try just plain esc..

Just in case someone wanted 1 binding to toggle, in this case I named below script toggle2, made executable & placed in $PATH. Set a custom binding of ctrl+x to run toggle2

```
#!/bin/bash
key_value=$(dconf read  /org/gnome/nautilus/preferences/always-use-location-entry)
echo $key_value | grep "false"
if [[ $? -eq false ]] ; then
dconf write  /org/gnome/nautilus/preferences/always-use-location-entry true
else
dconf write  /org/gnome/nautilus/preferences/always-use-location-entry false
fi

```

---

### Post by meetdilip on 2016-08-22
> **mc4man said:**
> Cool, I tried alot of keys, didn't think to try just plain esc..

Just in case someone wanted 1 binding to toggle, in this case I named below script toggle2, **made executable & placed in $PATH**. Set a custom binding of ctrl+x to run toggle2

```
#!/bin/bash
key_value=$(dconf read  /org/gnome/nautilus/preferences/always-use-location-entry)
echo $key_value | grep "false"
if [[ $? -eq false ]] ; then
dconf write  /org/gnome/nautilus/preferences/always-use-location-entry true
else
dconf write  /org/gnome/nautilus/preferences/always-use-location-entry false
fi

```

1. How do you make this executable

2. Placed in $PATH : How to do that ?

Thanks for the ctrl+ l and esc key suggestions.

---

### Post by mc4man on 2016-08-22
> **meetdilip said:**
> 1. How do you make this executable

2. Placed in $PATH : How to do that ?

Thanks for the ctrl+ l and esc key suggestions.
Well you could use a terminal & commands of mkdir, touch,gedit, chmod & source but I give you the gui method - 

Open your home folder > right click > New Folder >  name it
 bin

Open the bin folder > right click > New Document .. , name it something simple ending with a number, for example,  toggle2
 (- adding a number pretty much assures you're not using an existing linux command
Open the file in a text editor, paste in complete code box from above, save, close editor

Right click on the file > Properties > Permissions > click the Execute: box to enable.
Reboot, then open nautilus & a terminal. Type in the name of script, ex. toggle2, press enter,  the breadcrumbs should change to location. Press up arrow on keyboard to reload command, press enter, should go back. (may print false every other, doesn't matter..

If working then open System Settings > Keyboard > Shortcuts >  Custom shortcuts. Click the + ,  give the shortcut any name, for command use script name, ex. toggle2 , click apply - scr.1
After creating click on the "disabled" > use binding desired on keyboard to set. I used ctrl+z as it's one handed & apparently not taken. screen 2

To use,  just binding with or without focus on nautilus.
If you later have any other user scripts then just put them in the bin folder you created in home folder.
( marked as executable of course.

Edit:  ctrl+z binding better as ctrl+x is used by nano, maybe elsewhere. Point is to use a binding not used elsewhere

---

### Post by meetdilip on 2016-08-23
Thanks. So helpful :)

---

