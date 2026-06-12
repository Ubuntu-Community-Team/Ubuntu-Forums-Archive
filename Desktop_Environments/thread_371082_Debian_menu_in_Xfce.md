---
title: "Debian menu in Xfce"
date: 2007-02-26
forum: Desktop Environments
---

### Post by x1a4 on 2007-02-26
Hi,

How do I add the Debian menu to my Xfce menu?  

Thank you.

---

### Post by 5-HT on 2007-02-26
Install *menu *from the official repos and everything should be set up automagically. If not, you may need *menu-xdg *as well. 

HTH

---

### Post by x1a4 on 2007-02-26
> **5-HT said:**
> Install *menu *from the official repos and everything should be set up automagically. If not, you may need *menu-xdg *as well. 

HTH

Already have, no dice.  I also tried Alacarte but that's for GNOME menus only.

---

### Post by aidanr on 2007-02-26
xfce4-menueditor -> edit -> add external -> type system

that works for me, but i also have gnome installed so i'm not sure what extra you'd need if you're xfce only

---

### Post by x1a4 on 2007-02-27
> **aidanr said:**
> xfce4-menueditor -> edit -> add external -> type system

that works for me, but i also have gnome installed so i'm not sure what extra you'd need if you're xfce only

This just adds the standard menu items--already have that.  I want the _Debian_ menu.  

I've searched far & wide and it turns out that Xfce doesn't recognize the Debian menu files.  I even located all the *.menu files on my computer and added to my menu to no avail.  I also used *xdg-desktop-menu* to add all the *.directory and *.desktop files created by *menu* and *menu-xdg* but they were all dumped in Apps -> Other, creating one huge menu--undesirable.  I even created symlinks in /usr/share/applications to all directories containing the Debian *.desktop files and got the same result as when I used *xdg-desktop-menu*.  

As far as I can tell, the only way to add the Debian menu is to edit each individual *.desktop file by hand, and then either use *xdg-desktop-menu* or create symlinks in /usr/share/applications--too much hassle.  I'll just wait till the Xfce developers get their act together and fix the seriously flawed menu system in an otherwise fine DE.  I hope it's soon.

---

### Post by alnokta on 2007-10-21
sudo apt-get install menu
sudo apt-get install menu-xdg

update-menus
sudo update-menus

---

### Post by Galoot on 2007-10-29
> **alnokta said:**
> sudo apt-get install menu
sudo apt-get install menu-xdg

update-menus
sudo update-menus

But, for heaven's sake, back up [FONT="Courier New"][COLOR="Teal"]~/.config/xfce4/desktop/menu.xml[/COLOR][/FONT] first. You'll lose any customizations you may have made.

---

### Post by pstep9407 on 2008-01-15
Thanks very much!

---

