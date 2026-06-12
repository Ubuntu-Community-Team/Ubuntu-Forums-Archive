---
title: "getting to know the file structure"
date: 2006-08-12
forum: Desktop Environments
---

### Post by lonelypauly on 2006-08-12
many times i will install a program (dapper/gnome) and it wont show up under "Applications"...where are such programs stored in the file system...can I make shortcuts for any program...it seems that some will not allow me.

---

### Post by chavo on 2006-08-12
The apps don't really install into any one directory. They are split up.

Binaries go into /usr/bin
System wide configuration files go into /etc
Resources like icons or images, etc go int /usr/share

So if an app doesn't install an icon in the menu you'll find the binary in /usr/bin most likely. You can check by trying to run the app from the command line, if it's installed anywhere in your path it will launch.

---

### Post by jchau on 2006-08-12
If you want to know where the installed files are going, you can open Synaptic Package Manager, find the package, right-click on it, select properties, and switch to the Installed Files tab.

Once you find the file you want to create the "shortcut" (a symbolic link) for, you can create the symbolic link using the command:
```
ln -s target link_name
```
where target is where the symbolic link will point and link_name is where the link should be placed.  For example, if I wanted to place a "shortcut" to the program xclock on my desktop, I will first locate xclock using the command:
```
which xclock
```
and then I will create the link using the command:
```
ln -s /usr/bin/xclock ~/Desktop/
```

As for editing the menus, I am uncertain how to do that, but [this howto]("http://ubuntuforums.org/showthread.php?t=225390") seems to address it.

---

