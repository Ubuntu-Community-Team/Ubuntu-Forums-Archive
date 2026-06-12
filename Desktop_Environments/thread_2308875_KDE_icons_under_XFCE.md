---
title: "KDE icons under XFCE"
date: 2016-01-06
forum: Desktop Environments
---

### Post by koszyk.spamowy on 2016-01-06
Hi, 

I use Xubuntu with XFCE but I need Konsole and Krusader. And there is problem with icons. 
I want to change icons in Krusader, but KDE Control Panel is empty:
[http://www.zimagez.com/zimage/przechwycenieobrazuekranu2016-01-0611-41-07.php](http://www.zimagez.com/zimage/przechwycenieobrazuekranu2016-01-0611-41-07.php)
why? What should I install to setup in KDE application the same icons like in XFCE.

---

### Post by egeezer on 2016-01-08
To get the configuration options of a desktop environment such as icons, you need it to be completely installed, not simply present as a few isolated applications.  Your desktop environment is currently Xfce, and it is in control of the icon system for all the later-installed applications.

---

### Post by Sweet_Baby_Jamie on 2016-01-08
In Xfce panel you can edit all the icons by right-clicking the item and selecting Properties.  Then select Icon and instead of just choosing one from the default list ("application icons"), you can choose to select from "All Icons" and pick any one!  Your KDE icons may be among the choices.

---

### Post by koszyk.spamowy on 2016-01-14
> **egeezer said:**
> To get the configuration options of a desktop environment such as icons, you need it to be completely installed, not simply present as a few isolated applications.  Your desktop environment is currently Xfce, and it is in control of the icon system for all the later-installed applications.


No, this is not true. In previous version Xubuntu KDE Control Panel was OK and I've set the same icon-set to Krusader as in XFCE.

---

### Post by pedro-albarran on 2016-05-16
> **koszyk.spamowy said:**
> No, this is not true. In previous version Xubuntu KDE Control Panel was OK and I've set the same icon-set to Krusader as in XFCE.

It certainly seems that systemsettings (KDE Control Panel) used to be, but it is not longer useful unless the whole Desktop is installed.

A solution for changing icons in KDE applications can be found here: [http://askubuntu.com/questions/637051/ubuntu-15-04-change-kde-applications-icons](http://askubuntu.com/questions/637051/ubuntu-15-04-change-kde-applications-icons)

It seems that using kcmshell4 can be useful in general for other aspects of KDE applications.

---

