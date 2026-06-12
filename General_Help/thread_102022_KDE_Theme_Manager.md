---
title: "KDE Theme Manager"
date: 2005-12-11
forum: General Help
---

### Post by landcross on 2005-12-11
Can anyone tell me where I can find Theme Manager. I have installed KDE (almost everything in Kubuntu) but I cannot find this in package manager.
Could it just be a problem with my program menu not updating.

How do I update the program menu...or where I can I install KDE theme manager from

---

### Post by Knomefan on 2005-12-11
I think the problem is that it isn't shown in system settings.

However, you should find it in kcontrol, which is installed though it is hidden from the menu.
Just start kcontrol from a terminal and theme manager should be there.

---

### Post by landcross on 2005-12-11
Thanks that worked.... is there a way I can add this to the program Menu ?.


Also how do I may the program menu show everything installed..is there an update script?

---

### Post by Knomefan on 2005-12-11
Well, in theory it should show every (desktop)app you installed.
Kcontrol is just a special case because the kubuntu devs apparently decided to hide it and use system settings in stead (which probably requires kcontrol to be installed, I guess).

The easiest way to enable it is to edit the KControl.desktop file (these files are responsible for what is shown in the menus)
Just open up /usr/share/applications/kde/KControl.desktop with your favorite editor as root (for example: 
```
sudo nano -w /usr/share/applications/kde/KControl.desktop 
```)
scroll down to the end of the file and delete or comment out the following option:
Hidden=true

And that should be it.

---

