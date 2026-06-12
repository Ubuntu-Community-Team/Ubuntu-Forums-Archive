---
title: "nautilus not working, no desktop icons, cant open folders"
date: 2008-11-23
forum: Desktop Environments
---

### Post by ariel-bar on 2008-11-23
hey, i'm pretty new to linux so i'm always trying new thing...

so... i tried to change my default file manager from nautilus to dolphin.
didn't like it... so removed it and wanted to go back to nautilus...
when i restarted, suddenly i dont have a responding desktop (no icons and right click doesn't work) + when i try to open Home or anything else i get an error messege:

Could not open location 'file:///home/ariel'
No application is registered as handling this file

PLEASE HELP!!!

p.s, sorry for my bad english...

---

### Post by ajgreeny on 2008-11-23
If nautilus is still installed, right click on a folder using nautilus (Alt+F2 and enter the command _nautilus_ if needed) and then put a check mark in "Open Folder"

---

### Post by ariel-bar on 2008-11-23
when i try to load nautilus i'm getting:

"The program 'nautilus' is currently not installed.  You can install it by typing:
sudo apt-get install nautilus
bash: nautilus: command not found"

when i try to install:
using synaptic - nautilus is checked like its already installed
using terminal - "nautilus is already the newest version.
                  0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

---

### Post by ajgreeny on 2008-11-24
Try uninstalling nautilus and then reinstalling it using the terminal.

---

### Post by ariel-bar on 2008-11-24
i tried:

sudo apt-get remove nautilus
sudo apt-get autoremove

then i logged of and

sudo apt-get install nautilus

logged off again...

still doesn't work :'(
i'm about to go nuts!
i dont want to uninstall ubuntu because of such a silly thing ( like windows |-: )

---

### Post by ariel-bar on 2008-11-24
if it helps...

[http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)

i can tell you i used this script to try making konqueror default

and i tried the script to restore nautilus and got:
You're missing a Computer .desktop backup file--nothing to restore
You're missing a Nautilus .desktop backup file--nothing to restore
You're missing a folder handler .desktop backup file--nothing to restore
You're missing a Home .desktop backup file--nothing to restore
You're missing a Network backup file--nothing to restore. If you had Thunar as your previous default file manager, this is normal.
Nautilus should now be your new default file manager in Gnome again

I DONT THINK THATS A GOOD THING :-S

---

### Post by ariel-bar on 2008-11-25
someone please?

---

