---
title: "Recover Gnome Applications menu ?"
date: 2005-04-21
forum: Desktop Environments
---

### Post by goebbe on 2005-04-21
It seems that this is not my day.  :(
I manually deleted some files in the ~/.config
and the /etc/gdm folders (to delete the configuration files for 
Xfce)  and now  I lost all Applications entries in 
the Gnome-panel-menu (even for those applications which
are in the System tree)

I cannot figure out how I could recover the standard
menu entries for Ubuntu.  
Do I have to reinstall Ubuntu to get the menu entries? 
Any suggestions are welcome.

---

### Post by goebbe on 2005-04-23
Finally I found a solution for my problem:

1. logout from Gnome
2. str+alt+F1
3. login as root (first ubuntu user)
4. sudo /etc/init.d/gdm stop
5. sudo apt-get remove --purge gnome-menus
6. sudo apt-get install gnome-menus
7. sudo apt-get install ubuntu-desktop
8. sudo /etc/init.d/gdm start
9. login - and the standard applications menus are back

Just reinstall gnome-menus with synaptics (while logged in
in Gnome) did not work for me.

---

### Post by transistor on 2005-05-24
[COLOR=Blue]sudo apt-get install gnome-menus[/COLOR]

I have also lost my application menus and top and bottom bars. I now have a very clean looking desktop!

I can't find gnome-menus on my machine (standard Ubuntu install from CD). gnome-menus doesn't appear on Synaptic download either.

Any ideas?

Thanks.

---

