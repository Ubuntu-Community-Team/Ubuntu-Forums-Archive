---
title: "How to get Debian Menu back???"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Sokraates on 2005-12-07
I installed debian menus on my system an after a while deleted them by mistake, when editing K-menu.

Now I want to have debian menus back, but nothing works. Tried uninstalling, reinstalling, update-menus .. nada.

Does anyone have a suggestion?

---

### Post by Lambert on 2005-12-07
try 

sudo dpkg-reconfigure <name of program>

replace <xxx> with the name of the program

---

### Post by matthew on 2005-12-07
I think he is looking for a way to add the "Debian" menu as a menu item in Applications.

Install "menu" eiter via synaptic or
```
sudo apt-get install menu
```

Then at a terminal type
```
update-menus
```

---

### Post by Sokraates on 2005-12-08
Didn't help. :( 

@ matthew: Exactly, I want debian menus back as a menu item. the problem is, that I deleted the menu item once, when I was editing K-menu.

At that time I had the menus installed. Uninstalling and reinstalling unfortunately doesn't help.

It seems, that K-menu somewhere saved a setting saying "*user X doesn't want debian menus to be displayed in K-menu*" and this setting sticks.

@ Lambert: 

I don't know what happens, but 

```
$ sudo dpkg-reconfigure menu
```

makes my comp calculate for a few seconds, so obviously it is reconfiguring something. Unfortunately, ther's no dialog and debian menus are still gone. ](*,)

**Edit:**
Tried

```
$ sudo dpkg-reconfigure menu-xdg
```

and

```
$ sudo dpkg-reconfigure pdmenu
```

always followed by

```
$ update-menus
```

Still nothing. Drats!

---

