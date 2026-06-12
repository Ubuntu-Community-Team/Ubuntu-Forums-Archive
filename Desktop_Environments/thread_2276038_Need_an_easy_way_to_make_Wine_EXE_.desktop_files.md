---
title: "Need an easy way to make Wine EXE .desktop files"
date: 2015-04-29
forum: Desktop Environments
---

### Post by yoshii on 2015-04-29
Hello, 

I use Wine on Lubuntu.  I am interested in how to easily make some desktop shortcuts to Wine EXE applications.  I know how to right click on the Lubuntu menu items for the "create desktop icon".  But I want to make desktop icon shortcuts for windows programs I have installed.  Can you help me know how to do this?

---

### Post by kerry_s on 2015-04-30
install menulibre for a gui menu editor/creator, once it's in the menu, like you said, simple right click gets it to the desktop.

---

### Post by yoshii on 2015-05-01
> **kerry_s said:**
> install menulibre for a gui menu editor/creator, once it's in the menu, like you said, simple right click gets it to the desktop.

OK I'll try that I guess, but can it deal with WINE links to EXE's?

---

### Post by Tadaen_Sylvermane on 2015-05-01
.desktop files just issue a command, nothing more. So you would need to figure out the command to send to launch a specific .exe and put that in the .desktop file.

```
[Desktop Entry]
Name=Minecraft
Comment=Sandbox
Exec=java -jar /data/minecraft/Minecraft.jar
Terminal=false
Type=Application
Icon=/data/pictures/icons/Minecraft.png
Categories=Game;

```
example of my current minecraft.desktop. you would put the command on the Exec= line.

---

### Post by yoshii on 2015-05-01
OK, I installed menulibre and created a menu entry in the right category, and saved the results, but nothing shows up in the Lubuntu menu for it.  
I think this is because Lubuntu doesnt use Unity nor Xfce,but uses LXDE, right?

This would've probably worked in Ubuntu Studio, but then again, Ubuntu Studio already has a menu editor.  But Lubuntu has it's own different style.  And I think the .desktops end up in a specific folder like they do on Ubuntu Studio, but I'm not using Ubuntu Studio anymore, I'm using Lubuntu.  And I don't know where to look for the menu entries.  

I do know the format for .EXE's :  wine "[path to exe]" but I don't have the place or access to the .desktop files and I don't want to rely on the menu to get there.  
I also tried to create a Launcher for the panel, but it won't let me browse to files, only to categories of pre-defined applications.  I can't get to any wine programs except for notepad and FL Studio (because it installs well on it's own).  

Can anybody help me?

---

### Post by Tadaen_Sylvermane on 2015-05-02
Copy or move the .desktop file to ~/.local/share/applications. That will add them to the menus.

---

### Post by MikeCyber on 2015-05-02
playonlinux is dead simple. One click for a desktop icon. Having fun with Tomb Raider 2013 right now.

---

### Post by yoshii on 2015-05-03
> **Tadaen_Sylvermane said:**
> Copy or move the .desktop file to ~/.local/share/applications. That will add them to the menus.

Hey, thanks that path is helpful.  I just wish it was easier to do stuff without having to sudo.

---

### Post by kerry_s on 2015-05-03
> **yoshi2 said:**
> Hey, thanks that path is helpful.  I just wish it was easier to do stuff without having to sudo.

that is in your home folder, that is the exact same spot menulibre creates the *.desktop file to. no sudo needed, please don't use root unless told to do so.

some menus are created at start, you may need to log out & back in after you make your launcher. also make sure you click save after you create your launcher.

---

