---
title: "LXLauncher menu"
date: 2012-04-12
forum: Desktop Environments
---

### Post by spiralciric on 2012-04-12
Hi,
Can you help me understand this? I wanted to learn how lxlauncher's  menu work, before I can do something useful, so at first I edited just the <Menuname> (/etc/xdg/menus/lxlauncher-applications.menu)from Play to  Playing and down under <Menu><Name> did the same, restarted lxlauncher,  but it still says Play. I then tried something else, added under  menuname Office name, and did a copy of one whole  <menu></menu>, just changed under <name></name>  to Office, but it did not appear after save and restart. I am clueless  why nothing is happening. F1 or is this some kind of bug?
I am using latest lxlauncher 0.2.2.

---

### Post by Rodney9 on 2012-04-12
To add to the menu - [http://ubuntuforums.org/showthread.php?t=1529870&page=2](http://ubuntuforums.org/showthread.php?t=1529870&page=2)



For How-To's, Information and Screen-Casts on Lubuntu go to the

Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by spiralciric on 2012-04-13
No, that is for lxpanel and lxde menu. LXLauncher uses that as a base, but has its own xml file for tabs and what is in them. Documentation says that configuration is in the file I mentioned, unfortunately, that does not work.
I will ask on the link you provided as well, thanks.

---

### Post by spiralciric on 2012-04-14
Ok, figured this on my own.
/usr/share/desktop-directories holds .desktop files, rename them to rename tabs, and also edit them with leafpad and change Name
/etc/xdg/lxlauncher/gtkrc - change tab and font colors
/etc/xdg/menus/lxlauncher... - under category change what is inside that tab, and change <Directory> to point to file in desktop-directories to change icon and name.

Still there is no way to change background color or use a wallpaper for version 2.2. I saw this working for v1.6, but trust me, its not worth bothering.

---

