---
title: "No desktop items"
date: 2005-06-17
forum: Desktop Environments
---

### Post by noodle on 2005-06-17
Hi,

I really have two problems.

I deleted the KDE Trash bin in gnome (stupid) and I can't get it back in KDE. Also, I can't get the desktop to display Home in KDE. I'm new to this, please be nice to me. 

 :-?

---

### Post by Xian on 2005-06-17
[HERE](http://kudos.berlios.de/kf/kisimlar/tipsntrix.html#showtrash) is a method for getting the trash icon on your KDE desktop.

---

### Post by noodle on 2005-06-17
[QUOTE=Xian][HERE](http://kudos.berlios.de/kf/kisimlar/tipsntrix.html#showtrash) is a method for getting the trash icon on your KDE desktop.[/QUOTE]

Thanks for the reply. I tried using the instructions you suggested, however, the file trash.desktop is missing. I cannont find it anywhere. Any other suggestions? BTW, I have managed to make the Trash appear on the taskbar, however, I would still prefer it on the desktop.

---

### Post by noodle on 2005-06-17
Fixed the Trash problem.

trash.desktop was located in /home/username/.Trash 

I set hidden=false

then placed the file in /home/username/desktop/

Its back!

Still need help getting the home folder to appear on the desktop though. Anyone?!

---

### Post by noodle on 2005-06-18
Found a temp solution ;)

Create a new file: home.desktop in /home/username/Desktop

Use Kwrite, and add the following lines:

[Desktop Entry]
Type=Link
URL=/home/username/
Encoding=UTF-8
Icon=folder_home
Hidden=false
Name=Home
Comment=Users Home Directory

Change URL to point to your own directory. Save and close. 

This is only a temp solution. There should be a better way?!?!?

---

### Post by codejunkie on 2005-06-18
you can also open up /usr/share/apps/systemview/ and copy the file home.desktop and paste it in /home/username/Desktop hope this helps.

---

### Post by Xian on 2005-06-18
[QUOTE=codejunkie]you can also open up /usr/share/apps/systemview/ and copy the file home.desktop and paste it in /home/username/Desktop hope this helps.[/QUOTE]
Nice one. Got all the other goodies in there as well. :)

---

### Post by Jengu on 2005-06-18
> **noodle]Found a temp solution  said:**
> 
Type=Link
URL=/home/username/
Encoding=UTF-8
Icon=folder_home
Hidden=false
Name=Home
Comment=Users Home Directory

Change URL to point to your own directory. Save and close. 

This is only a temp solution. There should be a better way?!?!?
 A simpler way than making a .desktop file by hand for the home folder icon is to use the method builtin to kde You guys are overcomplicating it ;)

Right click the desktop, and select the option to make a link to a location. Make the location /home/youruser. Then make the icon kfm_home. No text file editing necessary :)

---

