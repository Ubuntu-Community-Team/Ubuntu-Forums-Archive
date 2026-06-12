---
title: "Default file browser"
date: 2010-06-27
forum: Desktop Environments
---

### Post by jamesgiles on 2010-06-27
Hi,

Somehow i managed to change my file browser to Konqueror from whatever the default is ( i haven't managed to find the name). Now when I open my home folder it opens with Konqueror. 

Interestingly enough if I open the computer that opens up simply in file browser. Does anyone know how to change back to the default as I prefer the look of it to Konqueror. 

Many thanks

JG

---

### Post by dv3500ea on 2010-06-27
Press alt-f2
Enter gconf-editor
Navigate to desktop/gnome/session/required_components
Right click on filemanager and click edit key
Change the value from konqueror to nautilus, which is the name of GNOME's default file manager

---

### Post by ajgreeny on 2010-06-27
Are you using gnome?

If so here is a script that you can save as restorenautilus.sh, make executable and then run, either by double clicking or in terminal.
```

#!/bin/bash
if [ -f /usr/share/applications/nautilus-computer.desktop.backup ]; then
  echo -e "\nRestoring Computer .desktop file\n"
  sudo cp /usr/share/applications/nautilus-computer.desktop.backup /usr/share/applications/nautilus-computer.desktop
else
  echo -e "\nYou're missing a Computer .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/nautilus.desktop.backup ]; then
  echo -e "\nRestoring Nautilus .desktop file\n"
  sudo cp /usr/share/applications/nautilus.desktop.backup /usr/share/applications/nautilus.desktop
else
  echo -e "\nYou're missing a Nautilus .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/nautilus-folder-handler.desktop.backup ]; then
  echo -e "\nRestoring folder handler .desktop file\n"
  sudo cp /usr/share/applications/nautilus-folder-handler.desktop.backup /usr/share/applications/nautilus-folder-handler.desktop
else
  echo -e "\nYou're missing a folder handler .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/nautilus-home.desktop.backup ]; then
  echo -e "\nRestoring Home .desktop file\n"
  sudo cp /usr/share/applications/nautilus-home.desktop.backup /usr/share/applications/nautilus-home.desktop
else
  echo -e "\nYou're missing a Home .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/network-scheme.desktop.backup ]; then
  echo -e "\nRestoring Network .desktop file\n"
  sudo cp /usr/share/applications/network-scheme.desktop.backup /usr/share/applications/network-scheme.desktop
else
  echo -e "\nYou're missing a Network backup file--nothing to restore. If you had Thunar as your previous default file manager, this is normal.\n"
fi
echo '
Nautilus should now be your new default file manager in Gnome again
'
```
It is also here as a .txt attachment which may be easier to save, rename and make executable.

---

### Post by jamesgiles on 2010-06-27
Hi, I managed to change it, although not by either of those methods, although I did try.

I went to the gconf file and nautilus was already defualt, I also tried the script but I'm new to Linux file systems and don't know how to make files executable.

As I now know the file manager is called nautilus i just opened a folder with open with and typed nautilus then put it as the default.


Cheers for your help anyway.

---

### Post by doublewitt on 2010-08-29
> **jamesgiles said:**
> Hi, I managed to change it, although not by either of those methods, although I did try.

I went to the gconf file and nautilus was already defualt, I also tried the script but I'm new to Linux file systems and don't know how to make files executable.

As I now know the file manager is called nautilus i just opened a folder with open with and typed nautilus then put it as the default.


Cheers for your help anyway.

that worked fine for me also - so simple... thanks

---

