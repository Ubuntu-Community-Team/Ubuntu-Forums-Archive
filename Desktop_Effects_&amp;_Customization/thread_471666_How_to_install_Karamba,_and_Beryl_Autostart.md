---
title: "How to install Karamba, and Beryl Autostart?"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by shazm on 2007-06-12
I put the "beryl-manager" command in session, by clicking "new", but beryl doesn't start at startup.
Could you help me there and at the setup for Superkaramba?
thanks

---

### Post by nyvalbanat on 2007-06-12
In KDE, I autostart beryl by creating the file ~/.kde/Autostart/beryl-manager.desktop with the following contents:

[Desktop Entry]
Name=Beryl Manager
Name[fr]=Gestionnaire Beryl
Comment=Setup Beryl
Comment[fr]=Configuration de Beryl
Exec=beryl-manager
Icon=beryl-manager.svg
Terminal=false
Type=Application
Categories=System;Application;X-Fedora;
Encoding=UTF-8


You should be able to create a similar file for Karamba (say, karamba.desktop) and set Exec=karamba [themes...].

---

### Post by nyvalbanat on 2007-06-12
Oh, wait - there's an easier way. You should be able to drag-and-drop any application to ~/.kde/Autostart... Anybody?

---

### Post by shazm on 2007-06-12
I do not have KDE

---

### Post by luckyd on 2007-06-12
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX)

---

