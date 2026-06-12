---
title: "Custom Application Launcher in Panel?"
date: 2010-07-26
forum: Desktop Environments
---

### Post by roger_1960 on 2010-07-26
Hi

Does anyone know how to create a custom application launcher in the panel in Lubuntu. The options which appear when right clicking the panel in gnome (Ubuntu) dont seem to be anywhere.

---

### Post by cavalier911 on 2010-07-26
LXpanel calls it "Application Launch Bar"
There are two installed,one to the right of the menu button with the browser,lxterm,buttons and the other to the extreme right with the power off button. Right click in those areas,chose Application Launch Bar settings,Add,select application.If the program didn't install a .desktop file in /usr/share/applications you have to make your own.Copy a .desktop file for a program of the same type,open it in text editor,use it as a template.Change path to executable,path to different icon,name,save as /usr/share/applications/programname.desktop

---

### Post by roger_1960 on 2010-07-27
Hi

Thanks Cavalier, thats pointed me in the right direction.

---

