---
title: "global menu setup"
date: 2010-12-07
forum: Desktop Environments
---

### Post by pdk on 2010-12-07
Global Menus
-------------
meerkat 10.10 

How to create a global menu entry manually ?????
Create a .desktop file in /usr/share/applications
create an icon in /usr/share/pixmaps
If you move the .desktop in and out of the applications directory, the menu entry will eventually fail on the desktop.
Creating an entry in /etc/xdg/applications.menu
<And>
<Filename>Program.desktop</Filename>
</And>
does not work
The entry will get overwritten when you update the menus via the top panel edit menus.
If you screwup the syntax the menu tree will disappear from the menu.
You can get it back by using the top panel edit menus.
Picasa creates a file in /etc/xdg/menus/application.merg
as well as creating a .deskop file and aa .directory file in /usr/share/desktop.-directories.
********************************************************************
<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
    "http://www.freedesktop.org/standards/menu-spec/menu-1.0.dtd">
<!-- Do not edit manually - generated and managed by xdg-desktop-menu -->
<Menu>
    <Name>Applications</Name>
<Menu>
    <Name>Graphics</Name>
    <Directory>Graphics.directory</Directory>
<Menu>
    <Name>Picasa</Name>
    <Directory>picasa.directory</Directory>
    <Include>
        <Filename>picasa.desktop</Filename>
        <Filename>picasa-fontcfg.desktop</Filename>
    </Include>
</Menu>
</Menu>
</Menu>
*************************************************************
Creating similar entries for Program as a test did not appear in the menu.
Using Ubuntu tweak, updating the applications list and installing the latest gnome-setings-daemon
appears to have fixed the problem.
gnome-settings-daemon2.32-0-0ubuntu3.1
You have to re login to get a change to show.

Fat Clients.
------------
I have loaded the latest gnome-settings-daemon.
If I move a .desktop in and out of a users home directory , the menu shows.
However if you log off and on it does not show.

HOW DOES THE MENU SYSTEM WORK ????
----------------------------------
Somewhere there must be a cache of the current Global Menu.
There must also be a 'scanner' that detects changes.
I need to be able to fire that 'scanner' when the ltsp client starts up.

PLEASE HELP !!!!!!!!!!!!!!!
It's becoming a Knightmare.
Peter

---

