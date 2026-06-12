---
title: "Can't Find my Dowloaded games"
date: 2005-01-22
forum: Gaming &amp; Leisure
---

### Post by Lynx on 2005-01-22
Hi all, I downloaded a few games from synaptic and I can't find where it put them, one would think that since they are games, they would have been put in the games file, but such is not the case. Any help would be greatly appreciated.

---

### Post by LongTooth on 2005-01-22
Open a terminal (Applications>System Tools>Terminal), key in 'whereis <packagename>'. You will get several results. Most of the time something like /usr/bin/gamename will showup. Or 'usr/local/bin/packagename'. Still at the terminal (or from the 'Run Application' window) type in the 'usr/bin/XXX and your program will start.  Keep an eye on what comes up when you do a 'whereis XXX'.

---

### Post by jensyt on 2005-01-22
Perhaps /usr/local/games or /usr/games ?

EDIT: Horray! Someone got in a post while I was reading once again...

---

### Post by ilari on 2005-01-22
[QUOTE=Lynx]Hi all, I downloaded a few games from synaptic and I can't find where it put them, one would think that since they are games, they would have been put in the games file, but such is not the case. Any help would be greatly appreciated.[/QUOTE]
 In Linux the applications are not installed in a specific folder as in Windows (eg. C:\Program Files\Adobe\Reader 7.0), but the files wil be scattered in multiple directories (eg. /usr/lib/gimp, /usr/share/doc/gimp, /etc/gimp etc.). Usually the application executable is installed in /usr/bin or /usr/local/bin, where it automatically belongs to the users path. You can start it by simply typing the executable name (eg. gimp).

If you want to know what files were installed with a Ubuntu-package, you can use synaptic to do that. Just select the wanted package, choose 'Properties', and browse 'Installed Files' tab. In terminal you can just type 'dpkg -L <package-name>' to see the installed files.

---

### Post by LongTooth on 2005-01-22
I like ilari's answer better then mine. Clear and concise.

---

### Post by jensyt on 2005-01-23
[QUOTE=LongTooth]I like ilari's answer better then mine. Clear and concise.[/QUOTE]

Mine being the worst of the three, I know. I was trying to make it relatively simple in that it seems most games go to one of the two directories. Well, at least the games I have are all there.

---

