---
title: "how to group aplications in the launcher"
date: 2012-01-29
forum: Desktop Environments
---

### Post by Rigodonize on 2012-01-29
I have Ubuntu 11.10 installed and I have downloaded the ubuntustudio-audio aplications.

I would love to have a folder in the launcher with all these audio apps together instead of having them all over the place like I have them now...

Any ideas??

Thanks in advance!!

---

### Post by mcduck on 2012-01-29
You can't do exactly that, the launcher panel doesn't support folders or menu items.

However if you edit a programs .desktop file by hand, you can add many items into a launcher's right-click menu. Clicking on the launcher itself would still open whatever program it's for, but at least you can add a bunch of related applications into the menu to save some space....

For example here's the contents of the .desktop file for my Minecraft launcher, and a pic of how it looks like (left-clicking on the icon in panel launches Minecraft, and I can launch the server and a mapping program from the right-click menu):
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/home/mcduck/Programs/Minecraft/creeper.png
Exec=/home/mcduck/Programs/Minecraft/minecraft.sh
Name[en_US]=Minecraft
Name=Minecraft
Icon=/home/mcduck/Programs/Minecraft/creeper.png

X-Ayatana-Desktop-Shortcuts=Server;Minutor;

[Server Shortcut Group]
Name=Minecraft Server
Exec=gnome-terminal -x /home/mcduck/Programs/Minecraft\ Server/mcserver.sh
OnlyShowIn=Unity

[Minutor Shortcut Group]
Name=Minutor
Exec=minutor
OnlyShowIn=Unity
```

---

### Post by Rigodonize on 2012-02-07
Well, I think that is a bit too much for me... I'm quite useless in Linux really...

Thanks for the help just the same. Appreciated.

---

