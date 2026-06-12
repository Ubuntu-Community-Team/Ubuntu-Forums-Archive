---
title: "Gnome desktop missing"
date: 2007-05-24
forum: Desktop Environments
---

### Post by stoli150 on 2007-05-24
Issue when I log on to gnome Nataulis starts and then a blank desktop. No panels no menus.

I was having problems with firefox and reinstalled it. Just before this happened. All I can do is log on gnome with terminal. 

I then downloaded KDE and now i can at least surf and run programms but i would like to be able to run on gnome.

Any help apreciated.

peace out
Stoli

---

### Post by pbw on 2007-05-24
start gnome-panel from term and see what it says.. Also, you can move/rename/backup your gnome dotfiles and then try logging in gnome fresh, and see if everything works fine. I'd suggest the same with firefox, it might be some extension, theme or config you installed.

-- pbw

---

### Post by stoli150 on 2007-05-24
What folder are they in? They being the dot files and where are firefox dot files?  

When I "start gnome-panel from term and see what it says" in need to insatall it it did and I was able to log on to gnome. However on the desktop menu under places/home,system entries are missing I think before I had home desktop system cd floppy under places menu. Me so happy at least I can now log on. thanks:popcorn:

---

### Post by pbw on 2007-05-25
No prob stoli, glad it helped :)

Your configuration files are all located in your home folder. In nautilus view hidden files and you'll see them, or in terminal type "ls -a ~/". I don't use gnome, but it should be pretty self explanatory on what you might like to try moving or deleting to return to default gnome behavior. Probably .gconf and .gnome2. Move whatever's obvious like i show below and try relogging in. Can't hurt, you can always move your settings back afterwards if it doesn't help things.

 To use a default firefox, in terminal type "mv ~/.mozilla ~/.mozilla.bak & firefox" and see what is displayed if firefox doesnt start properly.

Lemme know if that helps,

-- pbw

---

