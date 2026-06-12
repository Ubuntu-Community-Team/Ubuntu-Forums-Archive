---
title: "Manually created menu item in Gnome disappears from Gnome, Ubuntu 10.04 (64 bit).afte"
date: 2010-05-15
forum: Desktop Environments
---

### Post by mirloviev on 2010-05-15
My primary goal is to create menu entries visible to all users.  
 Here are the steps  which demonstrate the problem :
 

 Steps 0-8 just create a new menu item.
 
[LIST=1]
[*]Start with a newly installed     Ubuntu 10.04 (64 bit). Gnome.
[*]Select menu System     ->Preferences->Main Menu.
[*]Select &#8220;Applications&#8221; on the     left.
[*]Click on &#8220;New Menu&#8221; button.
[*]Enter &#8220;gksudo nautilus&#8221; in     both fields. Click&#8221;OK&#8221;.
[*]Select the &#8220;gksudo nautilus&#8221;     menu.
[*]Click &#8220;New Item&#8221;.
[*]Again (just for simplicity) in all     fields enter &#8220;gksudo nautilus&#8221;. A new item is created. You could     also see that the new menu and the item are available in the     Applications menu and work fine.
     The goal is to make this new menu     entry available for all users. As expected the steps above create     three files under my home directory:
[LIST=1]
[*]~/.local/share/applications/alacarte-made.desktop
[*]~/.local/share/desktop-directories/alacarte-made.directory
[*]~/.config/menus/applications.menu                 
         They now should be moved to a common         location which is accessible for all the users.
[/LIST]
     
[*]Iin accordance with the spec     ([http://standards.freedesktop.org/menu-spec/1.0/](http://standards.freedesktop.org/menu-spec/1.0/)),      **move** the alacarte-made.desktop file to directory     /usr/share/applications.
[*]Everything still looks and works     fine, just as expected. But here is the problem.
[*]**If you now reboot your 64 bit     system the menu item would not show up any longer. **The only way I     found to see the menu entry again is to open the     /usr/share/applications/alacarte-made.desktop file and to add a     space and save it. I tried to do a 'touch' on the file but it did     not help.
[*]The above steps work fine on my 32     bit Ubuntu 10.04 or in KDE. In both of these cases the menu item     stays there.
[/LIST]
 

 I am not sure if this is a problem with system configuration or some sort of a bug in the 64-bit OS version. Or maybe I am doing something wrong? I'd highly appreciate any  comments or clues.

---

### Post by bluetagpizza on 2010-05-17
I am experiencing exactly the same problem (also running 10.04 64-bit). The menu items disappear after logging out and logging back in.

I first noticed the problem with the menu item for "Getting Things GNOME!" which disappeared after I logged out. That menu item was not manually created.

---

### Post by masux594 on 2010-05-17
Same error here.. Installed NetBeans IDE and after a reboot, the icon disappeared.. The same thing when i installed vMware Workstation 7, when i reboot the icons disappear.. Only one question.. Why??

Sysc, A

---

### Post by mirloviev on 2010-05-17
Thank you for your comments. 

This confirms my suspicion that this must be a bug in Gnome/Ubuntu. 

I opened Bug #581838 at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) to track this problem.

Here is the link:
[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/581838](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/581838)

---

