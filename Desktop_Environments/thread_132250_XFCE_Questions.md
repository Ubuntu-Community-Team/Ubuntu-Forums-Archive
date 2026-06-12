---
title: "XFCE Questions"
date: 2006-02-17
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2006-02-17
First, sorry if I'm in the wrong section. I couldn't find any sub-forums for help with XFCE. I rather like this DE, but there a few problems I've been having with them.

1) Even though I've edited the XFCE menu to point the file manager to xffm, when I click it it still loads rox-file. I have the same problem with the Web Browser, which loads Konqueror. I would much rather have xffm as the default file manager and a firefox binary as my default web browser.

2) This one is probably very silly, but how do you install themes for XFCE?

---

### Post by amoser on 2006-02-18
Ok, first off, XFCE is weird like this, the menu on the task bar at the bottom of the screen is different the the menu when you left click on the desktop.  To edit the menu on the task bar, edit /etc/xdg/desktop/menu.xml.  As to install new themes for XFCE, XFCE is written in GTK, so find any GNOME themes that you like, and find the .deb package for them, and install through the command line.  That should take care of your problem.  If you have any more quetions, PM

~Alan

---

### Post by TheIdiotThatIsMe on 2006-02-18
The themes I found that I wanted to install was actually not under GTK but under XFCE on [www.xfce-look.org](www.xfce-look.org) :(

---

### Post by TheIdiotThatIsMe on 2006-02-18
Oh also does XFCE have the ability to use icons and launchers on the desktop, or do you need to use Idesk?

---

### Post by taurus on 2006-02-18
[QUOTE=TheIdiotThatIsMe]Oh also does XFCE have the ability to use icons and launchers on the desktop, or do you need to use Idesk?[/QUOTE]
Yes, you have to go with idesk if you want icons/launchers on your desktop.

---

