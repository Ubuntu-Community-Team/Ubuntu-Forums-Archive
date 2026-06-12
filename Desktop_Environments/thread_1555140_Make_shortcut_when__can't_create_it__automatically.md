---
title: "Make shortcut when  can't create it  automatically ..."
date: 2010-08-17
forum: Desktop Environments
---

### Post by nerka10 on 2010-08-17
ok, i'll show how to make shortcut, i found this way myself so ...

first you need aplication ... i'll make shortcut for gnome terminal ;)

ok open text editor and paste code ... i use gedit text editor .. 


[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=gnome-terminal
Comment=hi all ;D
Categories=Application;
Exec=/usr/bin/gnome-terminal
Icon=gnome-terminal
Terminal=false
StartupNotify=false

so, very easy to understand ... :) 

save it like "gnome-terminal.txt" , like name witch you wrote, so you think why txt file ? because then you can't create shortcuts like in gnome it can't create .desktop files ... 

next move this file to another folder, don't leave on desktop, and rename finally to "gnome-terminal.desktop" so thats all ... ;)

and don't forget make this link exucutable, you can do it right mouse click >> permissions>>"Allow executing file as program" 

you can make shortcuts yourself now, just rewrite aplication name and path ... :)

---

### Post by Iowan on 2010-08-17
From the Code of Conduct:> Please do not cross post, or post the same thing in multiple locations.
Your three other (duplicate) threads have been jailed.

---

