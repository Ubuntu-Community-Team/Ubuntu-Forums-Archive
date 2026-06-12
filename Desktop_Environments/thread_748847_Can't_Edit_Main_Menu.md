---
title: "Can't Edit Main Menu"
date: 2008-04-07
forum: Desktop Environments
---

### Post by Caz'ar Xiladys'varion on 2008-04-07
I can't edit the Main Menu (System->Preferences->Main Menu). Although selection, and moving things up/down works fine, none of the 'show' checkboxes work. Any ideas?

And if I can't fix this how do I get to the configuration editor otherwise?

---

### Post by jrib on 2008-04-08
What is the output of: ```
find ~/.config ~/.local ! -user $USER
```

---

### Post by Caz'ar Xiladys'varion on 2008-04-08
syth@syth-desktop:~$ find ~/.config ~/.local ! -user $USER
/home/syth/.config/menus/applications-merged/wine-Programs-Ventrilo.menu
/home/syth/.local/share/icons
/home/syth/.local/share/icons/c401_ventrilo.0.xpm
/home/syth/.local/share/desktop-directories
/home/syth/.local/share/desktop-directories/wine-Programs-Ventrilo.directory
/home/syth/.local/share/desktop-directories/wine-wine.directory
/home/syth/.local/share/desktop-directories/wine-Programs.directory
/home/syth/.local/share/applications
/home/syth/.local/share/applications/wine
/home/syth/.local/share/applications/wine/Programs
/home/syth/.local/share/applications/wine/Programs/Ventrilo
/home/syth/.local/share/applications/wine/Programs/Ventrilo/Ventrilo.desktop
syth@syth-desktop:~$

---

### Post by jrib on 2008-04-09
```
sudo chown -R $USER ~/.config ~/.local
``` to make those files owned by your user again

---

### Post by Caz'ar Xiladys'varion on 2008-04-09
thx!

---

