---
title: "navigation bar is showing up but ..."
date: 2012-12-19
forum: Desktop Environments
---

### Post by adym3333 on 2012-12-19
I hv ubuntu 10.10 ..... i installed update packages today ..... after that a dailog box showed up saying "You want to keep navigation bar " option button  were given was CANCEL & DELETE.
By mistake i pressed DELETE ,so now i hv restored the bar through following cmnds...

gonftool-2 --shutdown
rm -rf  ~/.gconf/apps/panel
pkill gnome-panel 

**So now the bar is showing up but when I minimize any window it wont show up in that bar and I hv to maximize it by selecting through using ALT+TAB.**.
WHAT is the solution ....??

---

### Post by zombifier25 on 2012-12-19
Try re-adding the Window List applet to the panel.

---

### Post by adym3333 on 2012-12-19
> **zombifier25 said:**
> Try re-adding the Window List applet to the panel.
I hv no idea what zombifier is talking about .... :confused:

---

### Post by zombifier25 on 2012-12-19
Right click on the bar, choose "Add to Panel", scroll down to "Windows List", click it and drag it to the bar.

(just a personal advice: Ubuntu 10.10 has reached End Of Life. You may want to consider moving to newer versions)

---

