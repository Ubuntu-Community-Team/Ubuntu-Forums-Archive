---
title: "where are Window Managers registered?"
date: 2017-02-07
forum: Desktop Environments
---

### Post by oui on 2017-02-07
Hi

I did install «ratpoison» and do not find it under the window managers proposed by the display manager.

a/ where can I find the list of the window managers registered in my system?

b/ can I add ratpoison myself? if not, what is to do (invoque some ready to use routine like «sudo update-locale LANG=de_DE.UTF-8 LANGUAGE» in case of changing locales/language)?

e/ window manager switcher on fly?

kind regards

---

### Post by vasa1 on 2017-02-07
> **oui said:**
> Hi

I did install «ratpoison» and do not find it under the window managers proposed by the display manager.

a/ where can I find the list of the window managers registered in my system?

b/ can I add ratpoison myself? if not, what is to do (invoque some ready to use routine like «sudo update-locale LANG=de_DE.UTF-8 LANGUAGE» in case of changing locales/language)?

c/ where can I find the list of the display managers registered in my system and how to select a new one?

d/ is perhaps a commando line display manager (script) existing and installable from Ubuntu depository?

e/ window manager switcher on fly?

kind regards

If the installation of a window manager provides a *.desktop* file, it maybe in */usr/share/xsessions*.

I have```
-rw-r--r-- 1 root root  157 Apr 11  2016 Lubuntu.desktop
-rw-r--r-- 1 root root  165 Apr 11  2016 Lubuntu-Netbook.desktop
-rw-r--r-- 1 root root 1507 Feb 27  2016 LXDE.desktop
-rw-r--r-- 1 root root  198 Oct 14  2015 openbox.desktop
```
Several window managers accept```
new_wm --replace
```where "new_wm" is the window manager one wants to switch to in an existing session.

Why won't```
sudo apt install ratpoison
```work?

I'm not sure that changing locales has anything to do with window managers.

Re. display managers, it's preferable for the sake of clarity and to help other users, to start a thread devoted to that issue.

---

### Post by oui on 2017-02-07
Hi
Thank very much Vasa!
I did erase the lines concerning the session manager from my 1st msg and open a new thread for display managers.
With your help, I did add an item ratpoison.desktop in /usr/share/xsessions, and really, ratpoison appears in the modified list of WMs and opens as expected (I am in ratpoison now ;-) !)
«I'm not sure that changing locales has anything to do with window managers.»
I use JWM with xfce4.appfinder (as debian menu does not take the special KDE applications in consideration! xfce4 does it and nothing to do excepted install and add a line in .jwmrc) instead of KDE. It is not optimal but what else!?!).

---

