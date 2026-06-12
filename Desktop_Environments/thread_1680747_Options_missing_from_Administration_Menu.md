---
title: "Options missing from Administration Menu"
date: 2011-02-03
forum: Desktop Environments
---

### Post by jiex on 2011-02-03
Hello
I've been searching the forum hoping to find a solution to this. 
Under  - > System/Administration/
I should see <<Printer>>, but it is missing. It seems other things in the list are also missing, but cannot work out what.

Is there some way to restore <<Printer>> to the <<Administration>> list?

Thanks for any assistance. Great forum.

---

### Post by PRC09 on 2011-02-03
For 10.10 you can right click system and select edit menus.You should find what you need in there, left pane under admin.Just put a check beside anything you need to add or uncheck what you dont need......

---

### Post by jiex on 2011-02-03
Hello PRC09
Thanks for the tip. I tried what you suggested, but the <<Printer>> option is not in that list. I'm completely flummoxed by this.....

---

### Post by PRC09 on 2011-02-03
Never seen that before so not much help I am afraid.May  be some info here.....

[http://ubuntuforums.org/archive/index.php/t-1575570.html](http://ubuntuforums.org/archive/index.php/t-1575570.html)

---

### Post by coffeecat on 2011-02-03
@jiex, have a look at PRC09's link. It may be that the package system-config-printer-gnome has been uninstalled somehow. If that is the case, I suggest you make sure  system-config-printer-udev is installed as well. It looks as though it might be important. 

You think other things might be missing from the Administration menu. Have you ever uninstalled any default applications? If you think some things are still missing you could try re-installing the package 'ubuntu-desktop' and see what happens. Ubuntu-desktop is a meta-package with all the default Ubuntu gnome packages as dependencies (not necessarily directly - sometimes dependencies of dependencies), so re-installing ubuntu-desktop is a useful way of re-installing default stuff that has gone missing for whatever reason.

---

### Post by jiex on 2011-02-03
PRC09 - many thanks for the pointer; and Coffeecat - many thanks for the advice. You were quite correct. I did remove some programs a few weeks ago - I think it was SAMBA, because it was not working - and reinstalled it. It now works, but that's when I noticed others programs were missing. So, I ran the sudo command you suggested and the deleted items, including printers, returned. 
Thanks again for your very prompt replies. Much appreciated.

Jiex

---

