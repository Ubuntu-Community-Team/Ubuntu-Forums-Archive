---
title: "Customising Desktop"
date: 2008-01-12
forum: Desktop Environments
---

### Post by murtaza on 2008-01-12
I need a step by step guide how to install themes. I have had ubuntu for a few days now. Also, i need to know what themes wont work with Ubuntu. For now, I need to know if my desktop could look like this. 
[http://www.kde-look.org/content/show.php/Kore+%26+More++BG+for+Kooldock%2BAWN+%2B+Icons?content=67013](http://www.kde-look.org/content/show.php/Kore+%26+More++BG+for+Kooldock%2BAWN+%2B+Icons?content=67013)

if not then i would likw to know who to make it look like this...

[http://www.gnome-look.org/content/show.php/Mac_OS_X_Leopard_for_Ubuntu_v1.0?content=73271](http://www.gnome-look.org/content/show.php/Mac_OS_X_Leopard_for_Ubuntu_v1.0?content=73271)

thanks

---

### Post by ajgreeny on 2008-01-12
The gnome one should work, but the kde one probably won't unless you have the kde desktop installed as well as gnome.

---

### Post by catach on 2008-01-12
That gnome theme (not the icons) looks like the one used in Ubuntu Studio.

[Here](http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/) is a guide for that, apparently.

---

### Post by murtaza on 2008-01-12
thanks...ok since i'm new to linux..how do u get kde..u can have gnome and kde both at once...

---

### Post by murtaza on 2008-01-12
how do u add widgets or desklets?

---

### Post by flying_icarus on 2008-01-12
You can install the kubuntu-desktop package, that should install everything needed for KDE to work. (i.e. "sudo apt-get install kubuntu-desktop" in a terminal). The installation procedures may ask you if you want to use gdm or kdm as the login-manager, pick the one you like. If you want to change it afterwards, i think "sudo dpkg-reconfigure gdm" should ask the question again. Then before logging in change the session to KDE if you want to start it.

And as for widgets and desklets... KDE used to have "superkaramba" for this (search for a package or look for it on kde-look.org), and gnome used to have "gdesklets" for it. Those are programs which manage the various desklets, who are usually installed separately (again, usually by downloading from kde-look.org and following the instructions in the archive). For the gnome-based gdesklets, you can try "sudo apt-get install gdesklets gdesklets-data".

Last time i checked, gdesklets were a lot more unstable than superkaramba, but that was some months ago. :) The other ways you can customize your desktop enviroment is by changing the window decorations (borders on windows), gnome/kde themes (buttons, scrollbars, etc), icon sets (what get's displayed for folders and various filetypes in your filemanager) and login-manager themes. Usually anything you download from kde-look.org or gnome-look.org should have some instructions in it on how to install and if anything additional is needed for it to work.

Anyway, be patient and have fun experimenting. :) You may also consider creating a new user account to test the various eyecandy stuff, just in case something doesn't work the way it's intended and you have trouble removing it. :)

---

### Post by murtaza on 2008-01-13
ok...thanks....I was planning creating two partitions one for ubunto and the other for freespire or any other linux with built in kde thats better than freespire....i'm mainly into desktop customization and just watching videos or listening and browsing online..

---

