---
title: "Debian Menu in GNOME"
date: 2006-08-11
forum: Desktop Environments
---

### Post by PathSpace on 2006-08-11
I was wondering how, if possible, to get the Debian menu in GNOME.  I see the option for it in the Alacarte menu editor, but there are no entries there and seemingly no way to activate it.  I have the program "menu" installed, but I cannot get any kind of regular Debian menu in GNOME.  If anyone has any ideas about this, I would appreciate it.  :)

---

### Post by kaamos on 2006-08-11
try the commands install-menu and update-menus

---

### Post by Jagot on 2006-08-11
```
sudo aptitude update
sudo aptitude install menu
```

---

### Post by PathSpace on 2006-08-11
It would seem that one of those two commands would work, but neither did.  I've just decided to give up on getting a full Debian menu and live with the one I have.  :p  Thanks anyway though.  :)

---

### Post by Jagot on 2006-08-11
It's in the universe repository.  If you still want the menu, then look at either of these links to enable that repository:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by PathSpace on 2006-08-11
Jagot, I had no problem installing "menu," it's just that it does not do anything.  :p

---

### Post by Jagot on 2006-08-11
OK, so you don't see the menu appear in your Applications menu?  Try restarting the panel:

```
killall gnome-panel
```

---

### Post by PathSpace on 2006-08-11
So far I tried:

*  install-menu
*  update-menus
*  killall gnome-panel
*  Alacarte menu editor
*  Restarting X and restarting computer

I think I'll just forget about it.  :p

---

### Post by sawjew on 2006-08-12
Use Automatix, it can install the debian menu for you.

---

### Post by catlett on 2006-08-12
To install the Debian menu in Ubuntu 
```
sudo apt-get install menu
sudo apt-get install menu-xdg 
update-menus
```

EDIT. If the issue still isn't resolved, it may be an Alacarte menu editor issue. Open alacarte and make sure when you select Application, Debian is checked off.

---

### Post by fragos on 2006-08-13
I installed menu a while back and it wasn't added to the menu.  A few days later, I boot daily, I noticed there it was and it works as advertized.

---

