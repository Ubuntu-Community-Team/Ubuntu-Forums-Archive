---
title: "edit main menu"
date: 2011-10-09
forum: Desktop Environments
---

### Post by rattskjelke on 2011-10-09
Is there an easy way to edit the main applications menu in Xubuntu?
I want to add Shutdown and Reboot to it.

---

### Post by ajgreeny on 2011-10-09
I don't think there is an easy way, as alacarte will not work properly in xubuntu, and will also probably pull in most of the gnome desktop as well.  However it can be done by manually editing existing, or making new application.desktop files in /usr/share/applications and ensuring that these files allow the item to appear in the menu.

See [http://ubuntuforums.org/showthread.php?t=731469](http://ubuntuforums.org/showthread.php?t=731469) for a bit more information on doing this.  The same thing is needed in LXDE, (Lubuntu) I think.

EDIT:
I have just found [http://sourceforge.net/projects/lxmed/](http://sourceforge.net/projects/lxmed/) about a menu editor for LXDE which works brilliantly in Lubuntu and I am going to try it in xubuntu as well;  you never know, it may also work well on that.

---

### Post by rattskjelke on 2011-10-09
I just installed lxmed and it seems to work but doesn't do what I want. As far as i can tell it only edits submenus not the main menu.

---

### Post by Toz on 2011-10-09
Here is a way of doing it by directly manipulating the menu files (command-line procedure):

1. Copy over the main menu to your profile:
```
cp /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu ~/.config/menus
```

2. Create a specific menu entry .desktop file for Shutdown:
```
mousepad ~/.local/share/applications/xfce4-session-shutdown.desktop
```
...with the following contents:
```
[Desktop Entry]
Version=1.0
Type=Application
Exec=xfce4-session-logout --halt
Icon=system-shutdown
StartupNotify=false
Terminal=false
Categories=System;X-XFCE;X-Xfce-Toplevel;
OnlyShowIn=XFCE;
Name=Shutdown
Comment=Shutdown the computer

```
...save the file.


3. Create a specific menu entry .desktop file for Reboot:
```
mousepad ~/.local/share/applications/xfce4-session-reboot.desktop
```
...with the following contents:
```
[Desktop Entry]
Version=1.0
Type=Application
Exec=xfce4-session-logout --reboot
Icon=system-restart
StartupNotify=false
Terminal=false
Categories=System;X-XFCE;X-Xfce-Toplevel;
OnlyShowIn=XFCE;
Name=Restart
Comment=Restart the computer
```
...save the file.

4. Add the items to the menu:
```
mousepad ~/.config/menus/xfce-applications.menu
```
There are two sections that need to be edited:

4a. Section <Include>:
After the last entry (<Filename>xfce4-session-logout.desktop</Filename>) in the <Include> </Include> section, add the following:
```

<Filename>xfce4-session-reboot.desktop</Filename>
<Filename>xfce4-session-shutdown.desktop</Filename>

```

4b. Section <Layout>:
After the last entry (<Filename>xfce4-session-logout.desktop</Filename>) in the <Layout> </Layout> section, add the following:
```

<Filename>xfce4-session-reboot.desktop</Filename>
<Filename>xfce4-session-shutdown.desktop</Filename>

```
...save the file.

5. Reload the desktop:
```
xfdesktop --reload
```

6. Profit.

I know its cumbersome, but a true xfce menu editor (garcon) is planned for 4.10.

---

### Post by rattskjelke on 2011-10-10
> **Toz said:**
> 
4. Add the items to the menu:
```
mousepad ~/.config/menus/xfce-applications.menu
```There are two sections that need to be edited:


Ok I started to do this and found that I don't have a *~/.config/menus/* folder but there is a text file called *~/.config/menus*. I guess I'll add the sections to it and see what happens.

---

### Post by Elfy on 2011-10-10
should be there if you did number 1

Copy over the main menu to your profile:
Code:

cp /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu ~/.config/menus

---

### Post by rattskjelke on 2011-10-10
OK I figured it out and got it to work.
Now I'm pissed because I tried to add the Places popup menu and apparently it is different and only works in a panel.

---

### Post by rattskjelke on 2012-04-26
Xubuntu 12.04 has an editable main menu!

Right click on main menu button
Properties
Edit Menu

Yay!

---

