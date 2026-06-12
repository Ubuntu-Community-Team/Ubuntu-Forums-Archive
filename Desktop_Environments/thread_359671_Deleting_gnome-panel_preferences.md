---
title: "Deleting gnome-panel preferences"
date: 2007-02-12
forum: Desktop Environments
---

### Post by Centx on 2007-02-12
I was tinkering around with adding the "custom menu" to gnome-panel, and was going remove it in favour for the original "GNOME menu". When i changed back to the original gnome menu, gnome-panel went into a crash-frenzy:
When i close bug buddy, gnome-panel restarts and crashes immediately when loading the Gnome menu, so i thought deleting this panel would solve it.

So i need to delete the top panel manually, because I cant use the right-click method, since it crashes before I can do anything.

thanks for reading, and if any more info is nessecary, please just ask.

---

### Post by bapoumba on 2007-02-12
Could you add a new user (see **man adduser**) and see if this new_user panel is okay. If so, this has to do with your user conf files (.gnome* or .gconf most probably). Try to rename these one by one to see which one is guilty.

---

### Post by Centx on 2007-02-12
I have moved all of these, (.gconf .gconfd .gnome .gnome2 .gnome2_private) and nothing worked. It didnt crash when I made a new user though, so I dont know whats could be wrong. It seems that it loads ok until it loads the Gnome menu, so I just assumed that deleting the upper panel would work, but I could always paste the bugreport if nessecary

---

### Post by bapoumba on 2007-02-12
Mmm ...
Have you got anything in /tmp ?
Should be cleared on an reboot.

---

### Post by Centx on 2007-02-12
tried that, seems like that worked in a way, but gnome-panel is still crashing when it loads the "GNOME menu" item.
The weird is that gnome-panel didnt crash when I logged in as the new user which also loaded that =/ 

attached the bugreport, if it is to any use.

---

### Post by Centx on 2007-02-12
Did a cheap fix :(  just made a new user and moved over all files, and configured it over again. it do work, but I didnt find out what was wrong though =/

On the positive side, I got a much more attractive desktop =)

---

### Post by kblood on 2007-02-18
I was having a similar problem, and I just managed to fix it by deleting two .recently-used files in my home directory.

It seems to crash when trying to load the list of Recent Documents, maybe the icons, I don't know.

I found this in another thread here in the forums, but I don't remember exactly where.

---

