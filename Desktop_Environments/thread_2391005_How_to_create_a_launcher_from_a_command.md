---
title: "How to create a launcher from a command?"
date: 2018-05-04
forum: Desktop Environments
---

### Post by Blix775 on 2018-05-04
Hello! I have been using Cinnamon for some time now and I came back to LXDE and so far I am liking it. I have been trying to make a launcher for Minecraft but I can't add it to the panel or the menu. I need to add the command ```
 java -jar /home/blix/.minecraft/launcher.jar
``` I would like to add it to both, the panel and the menu. I will also be needing to create a menu item for Eclipse since the installer doesn't normally create one.

---

### Post by kerry_s on 2018-05-05
leafpad ~/.local/share/applications/minecraft.desktop

put:
```
[Desktop Entry]
Type=Application
Name=Minecraft
Comment=Minecraft Game
Icon=minecraft
Exec=java -jar /home/blix/.minecraft/launcher.jar
Categories=GTK;Game;
```


see if that works, some commands have to be done from a script. so you would change the** Exec=/path/to/minecraft.sh**

minecraft.sh
```
#!/bin/sh
java -jar /home/blix/.minecraft/launcher.jar
```

---

### Post by Blix775 on 2018-05-05
> **kerry_s said:**
> leafpad ~/.local/share/applications/minecraft.desktop

put:
```
[Desktop Entry]
Type=Application
Name=Minecraft
Comment=Minecraft Game
Icon=minecraft
Exec=java -jar /home/blix/.minecraft/launcher.jar
Categories=GTK;Games;
```


see if that works, some commands have to be done from a script. so you would change the** Exec=/path/to/minecraft.sh**

minecraft.sh
```
#!/bin/sh
java -jar /home/blix/.minecraft/launcher.jar
```

I navigate to that folder and click on it and the game launches. But how do I add it to the menu or the panel? I need to create a menu entry for Eclipse next.

---

### Post by Dennis N on 2018-05-05
'Games' is not a valid category. It should be 'Game'. That should get it in the right place provided all the rest is ok.

---

### Post by kerry_s on 2018-05-05
> **Dennis N said:**
> 'Games' is not a valid category. It should be 'Game'. That should get it in the right place provided all the rest is ok.

fixed :D

---

### Post by kerry_s on 2018-05-05
> **Blix775 said:**
> I navigate to that folder and click on it and the game launches. But how do I add it to the menu or the panel? I need to create a menu entry for Eclipse next.

run this first command from terminal:
```

leafpad ~/.local/share/applications/minecraft.desktop

```

your text editor will popup, with a blank page, copy & paste this:
```

[Desktop Entry]
Type=Application
Name=Minecraft
Comment=Minecraft Game
Icon=minecraft
Exec=java -jar /home/blix/.minecraft/launcher.jar
Categories=GTK;Game;

```

save, it should now be in the menus, but you might have to log out & back in, not sure how menus are refreshed in lxde.
you can then add it to the panel like you do any other app.

---

### Post by Blix775 on 2018-05-05
Thanks! That fixed it. Anyway I can add a picture to it? 

:D

---

### Post by kerry_s on 2018-05-05
> **Blix775 said:**
> Thanks! That fixed it. Anyway I can add a picture to it? 

:D

i guess your icon set don't have minecraft icon.
just change the:
```
Icon=minecraft
```
replace minecraft with something in your icon set.

i'm using papirus icon theme it has the minecraft icon, that's why i put minecraft.
[ATTACH=CONFIG]279588[/ATTACH]

---

### Post by Blix775 on 2018-05-05
> **kerry_s said:**
> i guess your icon set don't have minecraft icon.
just change the:
```
Icon=minecraft
```
replace minecraft with something in your icon set.

i'm using papirus icon theme it has the minecraft icon, that's why i put minecraft.
[ATTACH=CONFIG]279588[/ATTACH]

Thanks a lot! I´ll go check them out. :)

---

### Post by kerry_s on 2018-05-05
you can copy those same settings for your eclipse launcher, just replace the entries with eclipse.

i'm currently making a trash icon for dash to dock, still working on the script to swap the icon from
Icon=user-trash
to
Icon=user-trash-full

but it's working.
[ATTACH=CONFIG]279589[/ATTACH][ATTACH=CONFIG]279590[/ATTACH]

---

