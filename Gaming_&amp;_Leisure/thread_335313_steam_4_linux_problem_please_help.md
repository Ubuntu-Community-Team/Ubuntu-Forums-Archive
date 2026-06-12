---
title: "steam 4 linux problem please help"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by jinxy1919 on 2007-01-10
When i install steam for linux i get this error at the end how you fix this please? says right click steam.exe  select properties go to compatiablility tab  uncheck run this application in compatability options

---

### Post by pay on 2007-01-10
Try changing your windows version to windows XP with winecfg

---

### Post by jinxy1919 on 2007-01-10
tyed that anyother suggestions

---

### Post by Enverex on 2007-01-10
Install Steam properly inside Wine rather than using "Steam4Linux" as it works fine in Wine these days.

---

### Post by jinxy1919 on 2007-01-10
Ok and what would be the correct way to install it into wine?

---

### Post by pay on 2007-01-10
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

---

### Post by Enverex on 2007-01-11
Unfortunately that guide is outdated and wrong. The 2 main parts that are wrong are the CVS bit and the "Mozcontrol" bit.

To download it go to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and follow the instructions.
The mozilla control is now done by grabbing "wine_gecko.cab" (Google it) and put it in "~/.wine/drive_c/Program Files" chdir to that folder and then run "cabextract wine_gecko.cab".

---

