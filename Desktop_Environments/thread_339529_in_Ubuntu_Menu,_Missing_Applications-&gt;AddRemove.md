---
title: "in Ubuntu Menu, Missing Applications-&gt;Add/Remove menu"
date: 2007-01-15
forum: Desktop Environments
---

### Post by moonhk on 2007-01-15
Dear Reader
In my ubuntu Menu. I found that missing Application->Add/remove option. How to add it back ?

moonhk

---

### Post by aidanr on 2007-01-15
right click on applications -> edit menus -> check the box beside add/remove

---

### Post by moonhk on 2007-01-16
Thank. I try using other backup to find the menu option It is "/usr/bin/gnome-app-install".
But this file missing on my hard disk. So I need following step

apt-get install ubuntu-desktop 
The menu reappear.

---

### Post by Ambimom on 2007-01-18
Wow, thanks moonhk!  I didn't understand why this disappeared and now it's back.:-k

---

### Post by tom56 on 2007-01-18
For future reference in case someone is searching on this (though I don't think this was the problem this time round) users who aren't in the admin group don't have "Add/Remove..." in their "Applications" menu.

---

### Post by kbright on 2007-01-27
I have a similar problem.  My application menu is completely empty.  The same in both normal ID and root.  I ran the update-menus and get the following.


keith@keith-dapper-T60:~$ update-menus
&#26410;&#30693;&#30340;&#37679;&#35492;&#65292;&#35338;&#24687;=&#28961;&#27861;&#24314;&#31435;&#30446;&#37636;(.local/)&#65306; File exists
install-menu&#65306;/etc/menu-methods/xdg-desktop-entry-spec-dirs&#65306;&#25918;&#26820;
update-menus[31796]: Script /etc/menu-methods/xdg-desktop-entry-spec-dirs returned error status 1.
Unknown error, message=Could not create directory(.local/): File exists
install-menu: /etc/menu-methods/xdg-desktop-entry-spec-apps: aborting
update-menus[31796]: Script /etc/menu-methods/xdg-desktop-entry-spec-apps returned error status 1.
keith@keith-dapper-T60:~$

any ideas?

---

### Post by ComplexNumber on 2007-01-28
> Could not create directoryi wonder if you're another who has had their menu directory changed to root ownership. if so fire up your terminal and type in the following:

sudo chown -R  keith:keith /home/keith/.local

---

