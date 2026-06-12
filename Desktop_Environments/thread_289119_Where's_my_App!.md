---
title: "Where's my App!"
date: 2006-10-30
forum: Desktop Environments
---

### Post by leona on 2006-10-30
Hi

I know this probably sounds like a basic problem.

I install programes via the package manager, but they don't appear in the
menu.

How do I getm them into the menu, if I don't know the application
execuatble name?

Its not as if the menu system itself is very user friendly, seems very
difficult to add / modify entries in it.

Am I missing something really basic, why can't I see the applications I
install?

Coming from a M$ OS where when you install and app it places an entry into
its menu, why isn't Ubuntu/GNOME doing this?

Any ideas, thoughts, welcome

Thanks

Leona

---

### Post by Henry Rayker on 2006-10-30
One thing you can do, to try to figure out the name of the app is to open the package manager back up, find the package you installed...right click on the package and select properties. There will be a Properties entry on the right click menu. If you click this and select the Installed Files tab (or similar) you can see everything that the app installed.

As for adding it to the menu, I have often wondered the same. One way to add the app to the menu is to right click the menu and "edit menu" or similar. [I'm really sorry about the "or similar"s...I'm not at home at the moment]. In this menu editor, you can add and remove items at will, I believe.

I think a reason they're not added by default could be due to different desktop environments (GNOME, KDE etc) having different menu structures, but that's just a guess.

I hope this helps somewhat.

---

### Post by ahaslam on 2006-10-30
A simple *killall gnome-panel* may do the trick, sometimes things don't appear in the menu straight away.

If that (or a reboot) doesn't help, you can find out the excecutable's name in Synaptic. Search for your package, right click - properties - installed files, should be installed in /usr/bin/ - see this example:

[ATTACH]18546[/ATTACH]

It's then just a case of creating a launcher in your menu using the Alacarte menu editor (test the command in a terminal first). Just add new entry and set it up like this:

[ATTACH]18547[/ATTACH]

I hope that helps.

Tony.

---

### Post by leona on 2006-10-30
Ok thank you guys, I will try getting the application name via the properties and adding it manually.
Do you think this is some that Ubuntu / GNOME will address later, this could lead to confusion / etc for end users if they have to add entries for every application they install, could be very tedious, one for the to do list I guess?

---

### Post by sam81 on 2006-10-30
Try installing the Debian menu, I'm not sure, but I think you need the "menu" package for getting it. After that from a terminal:
$ update-menus

and finally, you might have to add it to the Gnome menu going to System > Preferences > Menu Layout

I think it should be installed and configured by default, it's very useful.

---

### Post by CatKiller on 2006-10-30
> **leona said:**
> Do you think this is some that Ubuntu / GNOME will address later, this could lead to confusion / etc for end users if they have to add entries for every application they install, could be very tedious, one for the to do list I guess?

It's not an Ubuntu thing - it's entirely down to the developers whether they choose to include a .desktop file (for the menu entry) or not.

If you're interested, you may want to look at the [Desktop Entry]("http://http://freedesktop.org/wiki/Standards_2fdesktop_2dentry_2dspec") and [Menu]("http://freedesktop.org/wiki/Standards_2fmenu_2dspec") specifications from freedesktop.org.

---

