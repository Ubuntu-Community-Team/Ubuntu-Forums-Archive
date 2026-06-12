---
title: "Gnome classic side panel"
date: 2012-10-09
forum: Desktop Environments
---

### Post by skag on 2012-10-09
[LEFT]I'm running Ubuntu 12.04 on gnome classic (hate unity :razz: )

picture first: 

[http://imageshack.us/a/img822/5602/folderpanel.png](http://imageshack.us/a/img822/5602/folderpanel.png)

So as you can see I added a side panel just for folders-links (not apps)  and what I want to do is add Names under the "folder" icon... any  ideas?

thnx in advance :smile:[/LEFT]

---

### Post by ajgreeny on 2012-10-09
I don't think you can do that in a panel. If you want to add text to a link like that I suspect you will simply need to add separate launchers to the folders using nautilus.

There are several ways to do that in versions before 12.04, but I'm not sure how you do it in 12.04. However what you need is a **nautilus.desktop** file for each folder named the same as the folder itself, so try dragging a launcher for nautilus from the menu, then open the .desktop file it produces in gedit, which you will have to do by finding the real name of the .desktop file from ```
ls Desktop
```in terminal.  In gedit you can edit the name of the file and the exec used.
The file contains the following in 10.04
```
[Desktop Entry]
Categories=GNOME;GTK;System;Utility;Core;
Comment=Browse the file system with the file manager
[COLOR=Red]Exec=nautilus --no-desktop --browser %U[/COLOR]
Icon=system-file-manager
[COLOR=Red]Name=File Browser[/COLOR]
NoDisplay=false
OnlyShowIn=GNOME;
StartupNotify=true
Terminal=false
TryExec=nautilus
Type=Application
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Version=2.30.1
X-Ubuntu-Gettext-Domain=nautilus
``` so edit the lines I show in red to point to the folders you want and name the same as as the folder.

---

### Post by jerrrys on 2012-10-09
My first thought would be custom folders (folder icon) using gimp and just add the name on top of the folder.

---

### Post by ajgreeny on 2012-10-09
> **jerrrys said:**
> My first thought would be custom folders (folder icon) using gimp and just add the name on top of the folder.
I did also think of that but dismissed it as I thought the icons would need to be too big for most people; certainly would for me!

---

### Post by jerrrys on 2012-10-09
Same size, 3 or 4 letters.

---

### Post by skag on 2012-10-10
> **ajgreeny said:**
> I don't think you can do that in a panel. If you want to add text to a link like that I suspect you will simply need to add separate launchers to the folders using nautilus.

There are several ways to do that in versions before 12.04, but I'm not sure how you do it in 12.04. However what you need is a **nautilus.desktop** file for each folder named the same as the folder itself, so try dragging a launcher for nautilus from the menu, then open the .desktop file it produces in gedit, which you will have to do by finding the real name of the .desktop file from ```
ls Desktop
```in terminal.  In gedit you can edit the name of the file and the exec used.
The file contains the following in 10.04
```
[Desktop Entry]
Categories=GNOME;GTK;System;Utility;Core;
Comment=Browse the file system with the file manager
[COLOR=Red]Exec=nautilus --no-desktop --browser %U[/COLOR]
Icon=system-file-manager
[COLOR=Red]Name=File Browser[/COLOR]
NoDisplay=false
OnlyShowIn=GNOME;
StartupNotify=true
Terminal=false
TryExec=nautilus
Type=Application
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Version=2.30.1
X-Ubuntu-Gettext-Domain=nautilus
``` so edit the lines I show in red to point to the folders you want and name the same as as the folder.

I used gedit on the nautilus.desktop file and I can change the name but How can I change the exec in order to lauch from the path I want? (I see that gedit is not exactly necessary, it can also be done by "super+alt" right clicking on the launcher. but its more manual so I like it :P) 

thnx for your quick responses :)

---

### Post by skag on 2012-10-10
Naaah! erase the last! :P This panel doesnt want to have the folders named!! :P I put the launcher on the panel and it still got no name! I'll try the thing with the icons :)

---

### Post by ajgreeny on 2012-10-10
Yes, get rid of the panel.

You can not add text to a launcher in the panel unless the text is part of the icon itself.  To have both icon and text you will need a launcher icon on the desktop, not on the panel.

To get a launcher for a particular folder you need to use the command ```
nautilus --no-desktop /path/to/folder
```though I am not sure how necessary the **--no-desktop** option is

---

