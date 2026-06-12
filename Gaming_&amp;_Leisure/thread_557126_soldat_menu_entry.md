---
title: "soldat menu entry"
date: 2007-09-22
forum: Gaming &amp; Leisure
---

### Post by don durito on 2007-09-22
Hi,

i would like to write an soldat menu enry which should be located under Applications/Games/Soldat

I know that i have to create a .desktop file in /usr/share/app-install/desktop/ but i don't know how to write it using this wine command ```
wine /home/user/.wine/drive_c/Programme/Soldat/Soldat.exe&& xrandr -s 0
```

so if anyone can give me a hint or perhaps copie and paste his/her soldat.desktop file this would be awesome.

thanks in advance
don

---

### Post by Mr. T on 2007-09-22
When you installed Soldat, hopefully WINE was behaving itself enough to provide a shortcut in the WINE menu of the Applications menu. Sometimes it won't create the menu entry but most often it will, so hopefully you can use that if it exists and using the GNOME Menu Editor to move it to the games menu.

---

### Post by don durito on 2007-09-22
hi

thanks for your reply; 
1. yeah wine does create a menu entry but i need to start the game with this special flags &&randr -s 0 to make soldat change to my default resolution by closing the game.

2. i can't edit my menu with the gnome menu editor cause i am using xubuntu

but thanks anyway

yours 
don

---

### Post by don durito on 2007-09-24
Hi,

i tried to edit the supertux.deskotp file to work as my new soldat file. this is what i did:
```
 [Desktop Entry]
Type=Application
Version=1.4.1
Encoding=UTF-8
Name=Soldat
Name[en]=Soldat
GenericName=A sidescroll shooter
GenericName[en]=A sidescroll shooter
Comment=A mix between worms and counterstrike
Comment[en]=A mix between worms and counterstrike
Icon=/home/peter/.wine/drive_c/Programme/Soldat/banner.gif
Exec= wine /home/user/.wine/drive_c/Programme/Soldat/Soldat.exe&&xrandr-s 0
Terminal=false
StartupNotify=false
Categories=Application;Game;ArcadeGame
```

but this just won't work. I don't know whats wrong about this file so if anyonem can help me thanks.

---

### Post by reset3x on 2007-09-24
> **don durito said:**
> hi

thanks for your reply; 
1. yeah wine does create a menu entry but i need to start the game with this special flags &&randr -s 0 to make soldat change to my default resolution by closing the game.

2. i can't edit my menu with the gnome menu editor cause i am using xubuntu

but thanks anyway

yours 
don

In Xubuntu go to /home/your username/.local/share/applications/wine/Programs/

You will find the folder for your program with the .desktop files inside. You can edit them with mousepad. 

Hope this helps!!

---

