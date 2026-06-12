---
title: "Changing displayed Icon in Launcher"
date: 2011-05-12
forum: Desktop Environments
---

### Post by jerome1232 on 2011-05-12
Okay so I created a custom launcher for 2 wine programs on my desktop and dragged them to my launcher to add them. They were both using the default cup of wine icon.

The first one kept this icon, the second one changed to the default custom launcher icon for gnome. I have since changed them to the games real icons but they aren't changing in the launcher even after removing and re-adding it to the launcher.

So 2 things are happening here, it seems the launcher is unable to use the same icon multiple times, and the launcher is "remembering" the icon's somewhere separatly from what the custom launcher is saying the icon should be.

Screen shot should illustrate as well.

---

### Post by wojox on 2011-05-12
Did you create a ~/.local/share/applications/wine.desktop file and if so could you post it?

---

### Post by jerome1232 on 2011-05-12
No I did not, these files do exist at that location however.

```
jeremy@Farewell:~$ ls ~/.local/share/applications/
mimeinfo.cache               wine-extension-jpe.desktop
wine-extension-chm.desktop   wine-extension-jpeg.desktop
wine-extension-gif.desktop   wine-extension-jpg.desktop
wine-extension-hlp.desktop   wine-extension-png.desktop
wine-extension-htm.desktop   wine-extension-rtf.desktop
wine-extension-html.desktop  wine-extension-txt.desktop
wine-extension-ini.desktop   wine-extension-wri.desktop
wine-extension-jfif.desktop  wine-extension-xml.desktop

```

Should I create that file? Would it setup a custom icon for all wine programs? I was more hoping to create 2 separate icons for the 2 separate individual launchers.

---

### Post by wojox on 2011-05-12
See what this does:

```
cp /usr/share/applications/wine.desktop ~/.local/share/applications
```

```
gedit ~/.local/share/applications/wine.desktop
```

Have a look here for custom [Icons]("http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand")

---

### Post by jerome1232 on 2011-05-12
Copied it, this is it's contents.

```
jeremy@Farewell:~$ cat ~/.local/share/applications/wine.desktop 
[Desktop Entry]
Type=Application
Name=Wine Windows Program Loader
Name[cs]=Zavad&#283;&#269; program&#367; pro Wine
Name[de]=Wine Windows-Programmstarter
Name[es]=Wine Cargador de programas de Windows
Name[lt]=Wine Windows program&#371; paleidykl&#279;
Name[nl]=Wine Windows programmalader
Name[sv]=Wine Windows Programstartare
Name[ro]=Wine - Înc&#259;rc&#259;torul de programe Windows
Name[ru]=Wine - &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1095;&#1080;&#1082; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;
Name[uk]=Wine - &#1079;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1091;&#1074;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;
Name[fr]=Wine - Chargeur de programmes Windows
Name[ca]=Wine - Carregador d'aplicacions del Windows
Name[pt]=Carregador de aplicativos Windows Wine
Name[pt_br]=Carregador de aplicativos Windows Wine
Name[it]=Wine Carica Programmi Windows
Name[da]=Wine, Programstarter til Windows-programmer
Name[nb]=Wine - for kjøring av Windows-programmer
Name[nn]=Wine - for køyring av Windows-program
Name[sr]=Wine - &#1076;&#1080;&#1079;&#1072;&#1095; Windows &#1087;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072;
Name[sr@latin]=Wine - diza&#269; Windows programa
Name[hr]=Wine - diza&#269; Windows programa
Exec=cautious-launcher %f wine start /unix
MimeType=application/x-ms-dos-executable;application/x-msi;application/x-win-lnk;application/x-ms-shortcut;
Icon=wine
NoDisplay=true
StartupNotify=true

```

In case it's relevant these the .desktop files that I dragged onto the launcher.
```
jeremy@Farewell:~$ cat Desktop/World\ of\ Warcraft.desktop 
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Name[en_US]=World of Warcraft
Exec=wine '/media/F2E05E94E05E5EC3/Program Files (x86)/World of Warcraft/Wow.exe'
Comment[en_US]=Launch World of Warcraft under Wine
Name=World of Warcraft
Comment=Launch World of Warcraft under Wine
Icon=/home/jeremy/Downloads/WoW_Icon.png
```


```
jeremy@Farewell:~$ cat Desktop/StarCraft\ II\:Wings\ of\ Liberty.desktop 
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=wine
Name[en_US]=StarCraft II:Wings of Liberty
Exec=wine '/media/F2E05E94E05E5EC3/Program Files (x86)/StarCraft II/StarCraft II.exe'
Comment[en_US]=SC2
Name=StarCraft II:Wings of Liberty
Comment=SC2
Icon=/home/jeremy/Downloads/starcraft_2_-_lazy_launcher_gui_1.2-345873-1268118200.jpeg
```

---

### Post by wojox on 2011-05-12
The .desktop files you dragged in have two icon references try removing the top ones

Icon[en_US]=gnome-panel-launcher
Icon[en_US]=wine

 and log out and back in.

---

### Post by jerome1232 on 2011-05-12
Hahha, just noticed there are two icon specifications in there, will attempt to edit that.


And it worked, just a side note the multiple icon tags were created, I hadn't attempted to manually edit the .desktop files until now, seeing as they were automatically created I assumed they were correct and unity was messing up.

Thanks for the help wojox.

---

### Post by wojox on 2011-05-12
Your welcome. :P

---

