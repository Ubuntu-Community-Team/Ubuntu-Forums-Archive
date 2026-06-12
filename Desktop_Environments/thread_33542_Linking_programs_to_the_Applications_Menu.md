---
title: "Linking programs to the Applications Menu"
date: 2005-05-11
forum: Desktop Environments
---

### Post by Zorlaf on 2005-05-11
I am so happy with myself as my learning curve is almost complete. I can now add programs I have added network printers I have installed and configured Samba, Apache and tons of applications to start using them and familiarizing myself with them. I am getting very comfortable with terminals and writing with in shells (not as scary as the day I installed this amazing OS.) I am able to do upgrades updates and have learned and used Alien. I read the forums and do tons of research. My learning is bringing me to understanding of Linux and I am stoked!

I do have one small issue ... I can go into /usr/bin, or /usr/sbin and /usr/games I can see the binary files and I can launch them from there. I can enter a terminal and launch the programs I have installed no problem but some of the programs are not linking to the Applications menu and I am kind of stuck. I guess I could put them as quick launches in a drawr on the panel bar and select an icon for them but I really would like to understand and learn how to link them to the Applications menu. Some of the programs ex. Open Office 2.0b I have installed and did link to the Applications > Office menu on its own but others such as foobillards did not link to the menu's. 

Can some-one help me with this linking issue I am sure its a small over look on my part but I cannot seem to find anything about this topic anywhere in any documentation.

---

### Post by Zelut on 2005-05-11
Are you asking how to add the item to the gnome panel menu?  You can try this (if I understand your question correctly)...

(you'll need to change items with a * below to match your application.  Here is an example for adding the application LimeWire to the gnome panel menu:

sudo gedit /usr/share/applications/LimeWire.desktop

(copy/paste)

[Desktop Entry]
Name=LimeWire
Comment=LimeWire
Exec=runLime.sh
Icon=/opt/LimeWire/LimeWire.ico
Terminal=false
Type=Application
Categories=Application;Network;

You would edit:

sudo gedit /usr/share/applications/*Application.desktop

[Desktop Entry]
Name=*Application_name
Comment=*Application_comment
Exec=*/path/to/file (ie; /usr/bin/...)
Icon=*/path/to/icon
Terminal=false
Type=Application
Categories=Application;Games;

---

### Post by Zorlaf on 2005-05-11
This worked really well! Thank you. The program although in the Applications menu is not listed under "Games" it somehow lists under a new submenu "other" but it's in the Applications menu non the less and I don't have to click through to the binary to launch the programs I will now link all of my installed programs this way.  :)

---

### Post by Zelut on 2005-05-11
Hey glad I could help.  That's what the forum is for :)

Now just remember to check the forums & help out when you can as well.


None of us are as smart as all of us :)

---

### Post by mattgirv on 2005-05-11
[http://ubuntuforums.org/forumdisplay.php?f=67](http://ubuntuforums.org/forumdisplay.php?f=67) Try this handy project, :) Works well for me, and easier than the above method.

---

### Post by Zorlaf on 2005-05-11
Sweet deal now I can link my programs multiple ways graphically and from the command line. I do appreciate all the help.

---

### Post by simianMiscreant on 2005-05-11
nice! thanks.

---

