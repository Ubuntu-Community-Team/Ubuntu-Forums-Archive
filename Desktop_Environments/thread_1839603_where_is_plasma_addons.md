---
title: "where is plasma addons"
date: 2011-09-05
forum: Desktop Environments
---

### Post by tropdoug on 2011-09-05
I am trying to set up activities in 11.04 KDE. In this article [http://chakra-project.org/wiki/index.php/Plasma_Desktop_Basics#Desktop_Settings]("http://chakra-project.org/wiki/index.php/Plasma_Desktop_Basics#Desktop_Settings") it says that if you only have four activity template choices to add 'kdeplasma-addons-containments' from the repository. It doesn't say which repository though, and package manager indicates that 'kdeplasma-addons' is installed. 

1) How do I access the addons?
2) How do I get the containments because I want to do the grid   desktop?

I have also read that this version of Kubuntu and plasma suffers from crashing if you enable desktop effects - does this mean I can't load my Nvidia driver and compiz-fusion with cube rotation?

would appreciate some enlightenment

---

### Post by ankspo71 on 2011-09-06
Hi,
I could be mistaken, but I think the Grid and Grouping layouts/activities are new for KDE 4.7 (can anyone confirm that?). Do you have KDE 4.7 installed? Upgrading KDE can be done by visiting [http://www.kubuntu.org/news/kde-4.7](http://www.kubuntu.org/news/kde-4.7) . Upgrading can take a while to do, and problems might even occure, so make sure you have performed your necessary backups and wait to see if someone can confirm that Grid and Grouping layouts/activities are in fact new features for KDE 4.7.

Since I am using the development release of Kubuntu (Kubuntu 11.10), I have KDE 4.7 installed and the package 'kdeplasma-addons' installed and I can see the Grid and Grouping layouts/activities. 

> I have also read that this version of Kubuntu and plasma suffers from crashing if you enable desktop effects - does this mean I can't load my Nvidia driver and compiz-fusion with cube rotation?

The package nvidia-current in Kubuntu 11.04 contains a bug in the Nvidia graphics driver that freezes the desktop when terminal windows are resized/maximized/minimized on the KDE desktop if desktop effects are enabled. You could probably get around this if you do any of the following:

A. Use a terminal that doesn't resize/maximize/minimize such as "yakuake". 

B. OR use a PPA repository to install a more recent version of a Nvidia driver.

C. OR manually install the latest Nvidia driver. [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Hope this helps.

---

