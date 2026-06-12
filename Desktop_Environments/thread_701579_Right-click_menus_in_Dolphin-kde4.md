---
title: "Right-click menus in Dolphin-kde4"
date: 2008-02-19
forum: Desktop Environments
---

### Post by Burillo on 2008-02-19
[http://ubuntuforums.org/showthread.php?t=582536](http://ubuntuforums.org/showthread.php?t=582536)

There is a solution and it does work for dolphin KDE 3. But it does not work under KDE 4. Is there a way to add options to the context menus (apart from modifying the source-code)?

---

### Post by qpieus on 2008-02-19
I want to know the answer to this as well. According to some googling I did, service menus are supposed to work in dolphin. I'm not running KDE4, so I can't try it out, but what is occurring/not working when you try to make a new servicemenu in dolphin/KDE4?
I have a lot of custom servicemenus set up right now with konq/KDE 3.5.8. If I can't use them in dolphin, I can't see myself using dolphin at all.

---

### Post by Burillo on 2008-02-20
well, long story short, there is nothing at all. if you check out the link i given earlier you'll find the solution for servicemenus to work in Dolphin/KDE 3. but they don't work in KDE 4...

---

### Post by Burillo on 2008-02-20
the first image is for Dolphin/KDE3. The second one - Dolphin/KDE4

---

### Post by qpieus on 2008-02-20
I checked in the KDE bug tracker and came up with this:

[http://bugs.kde.org/show_bug.cgi?id=156476](http://bugs.kde.org/show_bug.cgi?id=156476)

> ------- Additional Comment #6 From David Faure 2008-01-24 13:48 -------
Dolphin and konqueror (in kde4) support the exact same servicemenus. However the syntax is indeed NOT
the kde3 syntax. Well, the syntax is pretty much the same but the location where to install the desktop files has changed.
kdesdk/scripts/qt4/Porting mentions the changes:

Servicemenus for konqueror and dolphin have moved to services/ServiceMenus/.
To port kde3 servicemenus you need to:
-> change installation rule so that it installs to ${SERVICES_INSTALL_DIR}/ServiceMenus
-> add KonqPopupMenu/Plugin to the ServiceTypes line 

---

