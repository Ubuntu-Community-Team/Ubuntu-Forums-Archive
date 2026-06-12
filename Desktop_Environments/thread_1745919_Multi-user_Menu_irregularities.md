---
title: "Multi-user Menu irregularities"
date: 2011-05-01
forum: Desktop Environments
---

### Post by Maineac54 on 2011-05-01
OS: Ubuntu 10.4 (Lucid)
Desktop: Gnome 2.30.2

I have this pc set up for myself as administrator and my two grandsons as regular users (not members of admin).  Note that none of us are a member of root.  It is intended primarily for playing games when they are at  my house.  I want to be able to have most of the same games available on all of our menus (system menu).

To accomplish this I 
* un-installed alacarte since it will not support differentiating system from user menus.  
* deleted the application.menu file in each users .config/menus folder
* deleted any *.desktop launch files in each users .local/share/applications folder
* deleted any *.directory files in each uses .local/share/desktop-directories folder
* checked the paths listed in XDG_CONFIG_DIRS and XDG_DATA_DIRS to be sure there were no menu related files in any folder other than the default locations (/etc/xdg/menus, /usr/share/applications, /usr/share/desktop-directories)
* edited the /etc/xdg/menus/applications.menu and appropriate launcher and directory files using gedit or nano to get the menu I wanted.
* set the owner and group of all *.desktop files in /usr/share/applications to root and the access to 644.

At this point the menu should work the same for all three of us, but it does not.  It works for me exactly as I expect it to.  For both grandsons, some of the games show up under "Other" in the menu and some don't show up at all.  At least one game launcher show's up on their menu that no longer exists on the system!

Can anyone explain this behavior or tell me how to correct it?  This is more than understanding the Freedesktop menuing system.  There is still more there that I am trying to understand and hope, some day, to develop a menu editing application to replace alacarte that will do a better job.  This is a fundamental Linux problem that I do not understand.  How could three different users be accessing the exact same files and not get the same results?

---

### Post by Maineac54 on 2011-05-02
I found the answer to this.  I had to reboot.  Funny, I don't associate having to reboot to implement configuration changes with Linux.

It is possible that xdg-desktop-menu forceupdate would have accomplished the same thing.  I'll have to try that first next time.

---

