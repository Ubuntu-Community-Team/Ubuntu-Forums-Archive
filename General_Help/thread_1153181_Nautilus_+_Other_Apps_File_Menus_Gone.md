---
title: "Nautilus + Other Apps File Menus Gone"
date: 2009-05-08
forum: General Help
---

### Post by kehon on 2009-05-08
the menus for apps like nautilus , eclipse, etc are gone so i cant change the preferences in nautilus and in eclipse well i'm just screwed there because i dont know how to get them back any help as soon as possible would be greatly appreciated

---

### Post by kanikilu on 2009-05-08
Did you by any chance install the Gnome Globalmenu applet and then not add it to your panel? It seems to be a very common cause for the "File Edit View [...]" menus to "disappear".

---

### Post by kehon on 2009-05-08
lol did that yesterday didnt like so uinstalled i thought / think not sure well hwo do i fix this

---

### Post by kanikilu on 2009-05-08
Try:
```
sudo apt-get remove gnome-globalmenu
```

If that doesn't work, check out this thread for other suggestions:

[http://ubuntuforums.org/showthread.php?t=987341](http://ubuntuforums.org/showthread.php?t=987341)

...wish people would stop suggesting this applet as a way to mimic OS X - it doesn't work with **all** applications, so it seems most people end up removing it from the panel and get in this situation with no menus...

---

### Post by kehon on 2009-05-08
i removed, reinstalled gtk, and restarted not working, looked in applets to add to panel and found it still there, so i added it gave back menus now i want to uinstall and i for some reason cant get it to uninstall, installed using ubuntu tweak and it said it had removed it

---

### Post by kehon on 2009-05-08
went back to ubuntu-tweak found the application in sidebar and did package cleaner found gnome-global menu and removed all things that sounded related to it that included gnome and global menu seems to work but gotta restart

edit:
yep that worked thanks very much for your help

---

