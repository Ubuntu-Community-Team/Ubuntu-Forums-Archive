---
title: "xubuntu application menu editing"
date: 2009-11-27
forum: Desktop Environments
---

### Post by zainka on 2009-11-27
Hi

I know this has to some ekstent been discussed a lot already but there is actually only one thing that *... make me annoyed ...* when it comes to xubuntu. This is the way it handles the menu editing of application menu. 

I would beleive that I should be posiible to use menu editing tool found in menu applications | settings | main menu , but nah. Prob. this is for the gnome menu only. However I found a thread on xfce wiki that theaced me to make the same editor work for editing xfce menues. 

Oooh yeah, how long was Adam in paradise? 

I understand now that Xubuntu is not completely xfce but has som additionals somewhere making some xfce tutorials useless, like for example how to edit application menu --> you can find the thread here [http://wiki.xfce.org/faq#menu](http://wiki.xfce.org/faq#menu) but the menu.xml files it referes to is not found in my system anywhere. I found a completely different way used for defining the menues which seems like using a lot of nested xml files.

I also found this blog [http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/](http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/) , but its from 2006 and not that usefull since it uses manual editing..

I am not totaly unfamiliar with xml's but i do not want to always edit it manually. Thats not what I wanna spend my days for. 

So question is simple, is there a way of editing application menu by GUI in xubuntu. As said. settings | main menu     does not work  .

Right now the application menu seems to live its own life, which must mean that xubuntu is really true A.I. , but it scares me a bit too. Where will it end?

Breg
Vidar

---

### Post by Brandon Williams on 2009-11-28
There is no graphical menu editor for the latest XFCE (the version in both 9.04 and 9.10). The links you posted both refer to the old menu format, and won't have any impact on the new menu format. The XFCE desktop has moved to the XDG menu system used by other desktop environments, like Gnome and KDE. Unfortunately, XFCE still doesn't have a graphical menu editor, so there's really not option but to edit the menu files manually.

---

### Post by zainka on 2009-11-28
Sounds like a bad idea to me, to bad i do not have the knowledge to write or rewrite existing amenu editing apps to do so. Would require to much time. Tried quite a few wm's in the past and found xfce to be the one best fitting my needs, simple and lightweight, but the mess in appmenu makes it look a bit unpro and annoyes me a bit(more).

May be able to live with it though.

Would it be dificult to rewrite alacarte to do the job?? Must think of it...
some info : [http://packages.ubuntu.com/hardy/all/alacarte/filelist](http://packages.ubuntu.com/hardy/all/alacarte/filelist)

---

### Post by demosthenese on 2009-11-28
alacarte editing is coming in xfce4.8

[http://jeromeg.blog.free.fr/index.php?post/2009/02/17/What-can-we-expect-in-Xfce-4.8-For-the-menu...]("http://jeromeg.blog.free.fr/index.php?post/2009/02/17/What-can-we-expect-in-Xfce-4.8-For-the-menu...")

---

### Post by Brandon Williams on 2009-11-28
> **zainka said:**
> Would it be dificult to rewrite alacarte to do the job?? Must think of it...

Unfortunately, Xfce-4.6 doesn't fully implement the freedesktop.org menu system, so modifying alacarte in order to use it for Xfce-4.6 is not trivial. Also, alacarte assumes that you have two menu files: applications.menu and settings.menu, but Xfce-4.6 uses one called xfce-applications.menu.

It's probably just better to wait for Xfce-4.8.

---

### Post by UbuntoJO on 2009-11-28
All of the menu items are represented by .desktop file in usr/share/applications.  That where I go to change an icon, add a menu item, etc.

---

### Post by sakisds on 2009-11-29
I installed the latest XFCE(or maybe not the latest because i used xubuntu-desktop) on my kubuntu installation(without recommends) and still i have a menu editor by right clicking -> Edit Application Launcher.

---

### Post by Brandon Williams on 2009-11-29
> **UbuntoJO said:**
> All of the menu items are represented by .desktop file in usr/share/applications.  That where I go to change an icon, add a menu item, etc.

You should avoid editing the items in /usr/share/applications. Instead, copy the file to ~/.local/share/applications and edit it there. On a single-user system, it's also best to add new items in that directory, too. Only add or edit items in /usr/share/applications if all users need your changes.

Also, adding new items to existing menus and editing existing items should work with alacarte. It will create or modify the desktop items for you, creating the necessary files in .local/share/applications. Just remember that you can't modify the menu structure (reorder, add, or remove menus), and you probably can't hide existing menu items.

---

### Post by zainka on 2009-11-29
Okay, Thanks to all. I will look into the mentioned tweaks and else wait for 4.8 (but what happend to 4.7??? Current is 4.6.1 Does this mean we have to wait long for 4.8 to come out, and what aboute xubuntu not using regualr xfce but some xdg or something?)

Breg
Vidar (Z)

---

### Post by Brandon Williams on 2009-11-29
> **zainka said:**
> but what happend to 4.7??? Current is 4.6.1 Does this mean we have to wait long for 4.8 to come out, and what aboute xubuntu not using regualr xfce but some xdg or something?

Xubuntu does use regular xfce. Xfce is moving in the direction of greater compliance with freedesktop.org standards (a.k.a. xdg). The problem is that this work isn't finished yet, so some xdg related tools (like alacarte) don't work yet. The next stable release (4.8) should have a more complete implementation of the xdg menu specification, and so is expected to work better with other tools.

4.7 is the development version, and 4.8 is the release version, which is scheduled to be ready in April-2010, which will hopefully mean that it's ready Xubuntu release 10.10.

---

### Post by Kangarooo on 2010-06-20
also .local/share/applications/ if some menu items are not in /usr/share/applications/

---

