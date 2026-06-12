---
title: "How Do I Uninstall Quake 3"
date: 2007-11-23
forum: Gaming &amp; Leisure
---

### Post by jonward690 on 2007-11-23
I installed it and I do not like it so how would I remove the game

---

### Post by Sockerdrickan on 2007-11-23
You can remove the dir you installed it to I guess, also there's a hidden dir created in your home folder which contains savegames etc

---

### Post by Scott O'Nanski on 2009-03-02
> **Tux0r said:**
> You can remove the dir you installed it to I guess, also there's a hidden dir created in your home folder which contains savegames etc

Just find the directory and delete it? Will that completely remove it from his system without any trace of the installation left behind afterwards?

---

### Post by cguy on 2009-03-03
Haha!

Just Noticed this thread is from 2007.

----------------


Generally, yes. But you could always search the entire file system for traces.
Search for files & folders containing "q3", "quake" or "pk3".

One way to do this is to open a terminal and issue commands like:
**locate** quake
or
**locate** quake
and it will output all the places you can find files containing "quake" in their names.
***Note:*** you must be in the root folder "/" in order to search for files everywhere.
If you are in /home/yourUserName, locate will only find the files living in the "yourUserName" folder and it's children.

Or you could open a file system browser (eg: nautilus), go in the root directory (type "/" in the location bar and press enter) and do a **Windows style search**.

Note that you need **super-user** access to remove files which are not in your home folder.
eg: **sudo** rm quake3
in console to remove a file named quake3
or
**sudo** nautilus
to open a nautilus window inside which you can delete any file you desire.


Addendum: your custom settings of quake 3 (and, generally, any program) can be found in a hidden folder in your home folder. Hidden folders' names are preceded by full stop (".").

So, for quake 3, this folder is
/home/yourUserName/.quake3
or
/home/yourUserName/.quake
or
/home/yourUserName/.q3
or
something else :)

Almost forgot: the desktop's menu entries can be deleted using the facilities provided by your Desktop Environment (eg: in Gnome, right click the main menu and choose Edit menus)

---

