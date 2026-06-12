---
title: "Xubuntu 14.04 Applications Menu: how to move items out of &quot;top level&quot; section"
date: 2014-07-11
forum: Desktop Environments
---

### Post by Kirkx on 2014-07-11
I'm trying to get rid of the "top level" section of my Applications Menu and move all four items that are still there to a custom Xubuntu category:

[http://i.imgur.com/lum8spb.png](http://i.imgur.com/lum8spb.png)
(please left click on the screenshot web page to get it to 100% zoom)
[http://i.imgur.com/GPkFf6q.png](http://i.imgur.com/GPkFf6q.png)

In Windows it would be a no brainer that takes about a minute, but Xfce is a different beast. I have spent a while on google and I'm aware of the following files that might have to be modified:

1) Menu Files

- the default Xubuntu menu file:
  /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu

- no idea about this one:
/etc/xdg/menus/xfce-applications.menu

- if the following file exists it overrides the default one mentioned above:
  /home/user_name/.config/menus/xfce-applications.menu

- the file should be edited with the "user account", not root (is this really true?)

2) Desktop files

- the default Xubuntu desktop files (extension not shown):
   /usr/share/applications/abiword.desktop
   etc.

 - if the following file exists it overrides the default one mentioned above:
   /home/user_name/.local/share/applications/abiword.desktop

 - the files should be edited with the "user account", not root (is this really true?)

I have tried to remove X-XFCE;X-Xfce-Toplevel in ubuntu-software-center.desktop file but it was always recreated with defaults.

[http://i.imgur.com/uuBvp13.png](http://i.imgur.com/uuBvp13.png)

[http://i.imgur.com/B3PqxXC.png](http://i.imgur.com/B3PqxXC.png)

I've been using MenuLibre that comes pre-installed with Xubuntu 14.04, I might have to try Alacarte.

---

### Post by Toz on 2014-07-11
> **Kirkx said:**
> 1) Menu Files
> - no idea about this one:
/etc/xdg/menus/xfce-applications.menu
This is the default Xfce menu file. The one used is based on the order of precedence of the XDG_CONFIG_DIRS environment variable:
```
$ env | grep XDG_CONFIG_DIRS
XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu:/usr/share/upstart/xdg:/etc/xdg:/etc/xdg
```
...therefore the default menu file in Xubuntu is found at /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu

> - if the following file exists it overrides the default one mentioned above:
  /home/user_name/.config/menus/xfce-applications.menu

- the file should be edited with the "user account", not root (is this really true?)
Yes, if you want to edit the user's menu file. If you want to edit the default system-wide menu file, you should edit /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu (as root) but keep in mind that those user accounts that already have ~/.config/menus/xfce-applications.menu will continue to use that file and not the root one.

The general practice should be to copy /etc/xdg/xdg-xubuntu/menus/xfce-applications.menu to ~/.config/menus and edit that file (as user).

> 2) Desktop files

- the default Xubuntu desktop files (extension not shown):
   /usr/share/applications/abiword.desktop
   etc.

 - if the following file exists it overrides the default one mentioned above:
   /home/user_name/.local/share/applications/abiword.desktop

 - the files should be edited with the "user account", not root (is this really true?)
If you want to edit the system-wide .desktop file, edit the file in /usr/share/applications (as root). If you want to make the change only for the current user, copy the .desktop file to ~/.local/share/applications and make the changes to that file (as user).

> I have tried to remove X-XFCE;X-Xfce-Toplevel in ubuntu-software-center.desktop file but it was always recreated with defaults.

[http://i.imgur.com/uuBvp13.png](http://i.imgur.com/uuBvp13.png)

[http://i.imgur.com/B3PqxXC.png](http://i.imgur.com/B3PqxXC.png)

I've been using MenuLibre that comes pre-installed with Xubuntu 14.04, I might have to try Alacarte.
To remove "Ubuntu Software Menu" from the Toplevel, you need to edit ~/.config/menus/xfce-applications.menu and remove the 2 instances of ubuntu-software-centre.desktop from the "Include" and "Layout" sections of the file. You also need to remove "X-XFCE;X-Xfce-Toplevel" from the Categories section of the ubuntu-software-center.desktop file.

Yes, it is confusing.

---

### Post by Kirkx on 2014-07-13
Thanks a lot, Toz. I really appreciate your replies and detailed explanations. I have just booted to my Linux Lite v2.0 and it turns out it has Alacarte Menu Editor instead of MenuLibre (according to Synaptic it's v3.10.0). With Alacarte's GUI, I could remove all top level menu entries, rename and move menu items around without problems. Also, the entries were automatically sorted in alphabetical order. Here are a few screenshots.

[http://i.imgur.com/AC5KXlC.png](http://i.imgur.com/AC5KXlC.png)
(please left click on the screenshot web page to get it to 100% zoom)

[http://i.imgur.com/vSEHzji.png](http://i.imgur.com/vSEHzji.png)

[http://i.imgur.com/Jv6EPl0.png](http://i.imgur.com/Jv6EPl0.png)

[http://i.imgur.com/XYO1hKH.png](http://i.imgur.com/XYO1hKH.png)

[http://i.imgur.com/dSt7W11.png](http://i.imgur.com/dSt7W11.png)

[http://i.imgur.com/rIsIE7P.png](http://i.imgur.com/rIsIE7P.png)

[http://i.imgur.com/0iKYMkb.png](http://i.imgur.com/0iKYMkb.png)

[http://i.imgur.com/R47Vyay.png](http://i.imgur.com/R47Vyay.png)

[URL="http://i.imgur.com/kWWaMVm.png"]http://i.imgur.com/kWWaMVm.png

[/URL][http://i.imgur.com/j5woOQp.png](http://i.imgur.com/j5woOQp.png)

[http://i.imgur.com/VDc5mS9.png](http://i.imgur.com/VDc5mS9.png)

---

