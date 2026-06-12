---
title: "Gnome Panel question."
date: 2005-04-02
forum: Desktop Environments
---

### Post by telmo on 2005-04-02
I've recently tried to edit/remove some annoying menus in the Gnome panel, so i visited [wiki](http://www.ubuntulinux.org/wiki/GnomeMenuEditingHowTo/view?searchterm=gnome%20menu) where i found out how to do it (since i couldn't with MenuEditor). So i opened gedit with sudo and changed the .desktop entries in /usr/share/applications as i pleased. But the thing is...they say to restart the panel after the changes, and i have no idea how to do that.
I tried rebooting and even removing the MenuBar from the panel and inserting it again... But it's all the same. The icons persist in the same place.

Anyone knows how to restart the damn panel? thx

---

### Post by kassetra on 2005-04-02
[QUOTE=telmo] The icons persist in the same place.
Anyone knows how to restart the damn panel? thx[/QUOTE]

Typically a reboot or a log out log back in restarts the panel...
Or you can even do a "killall gnome-panel" and then restart it with a "gnome-panel" - both commands you do in the terminal window...

Since you've rebooted already, the only thing I can see is that maybe what you're doing to change your menu is not what you think you're doing.

Editing the .desktop files will only change the applications - not the menu directories, for those, you also need to edit the .directory files... but then again, I'm not exactly sure what you're trying to remove.

---

### Post by telmo on 2005-04-02
I have two extra menus in my gnome menu. One is called 'Other' where my armyops game installed (i wanted it in games of course.), and the other is 'Internet'. I have two 'Internet' menus. When i install D4X (downloader for X) it creates the second 'Internet' Menu. 

Any idea in how to remove 'Other' and how to put D4X in the right 'Internet' menu?

thx

---

### Post by kassetra on 2005-04-02
[QUOTE=telmo]I have two extra menus in my gnome menu. One is called 'Other' where my armyops game installed (i wanted it in games of course.), and the other is 'Internet'. I have two 'Internet' menus. When i install D4X (downloader for X) it creates the second 'Internet' Menu. 

Any idea in how to remove 'Other' and how to put D4X in the right 'Internet' menu?

thx[/QUOTE]

You might want to post both of the .desktop files (one for armyops and one for d4x) here so I can see them, but that is where the problem lies -- they're calling to be put into special directories...

---

### Post by telmo on 2005-04-02
Here is D4X .desktop file:
(I found out that instead of being categorized as 'Application;Network;',  it's 'Application[COLOR=Red]s[/COLOR];Network;' as you can see below)

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=D4X

Type=Application
Comment=Download Manager
Exec=d4x
Terminal=false
[COLOR=Red]Categories=Applications;Network;[/COLOR]
Icon=/usr/share/pixmaps/nt.png
GenericName[en_PT]=

And the problem with Armyops (as well as Enemy Territory) is that the .desktop entries are in /usr/gnome/apps/games instead of /usr/applications. (sorry i didn't specify that in the first post.)

---

### Post by telmo on 2005-04-03
:-&

---

### Post by exphiles on 2005-04-10
I added an application on the gnome "Applications" menu and couldn't remove it. I searched everywhere and finally was able to remove it by going to /home/user/.local/ and removing the app.desktop file there.

That could help.

---

