---
title: "Global menu issue"
date: 2014-01-03
forum: Desktop Environments
---

### Post by elsandkls on 2014-01-03
Global menu does not allow localization of menus in individual applications, ubuntu 13.10, toshiba satelite laptop. 
Founds lots of posts about running "apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt" in older versions.
In 13.10 it reports that two of the programs were not installed, the third and it's supporting items were removed.
This did not correct the global menu behavior in any application.

My screen is in the process of dieing, and while I search for replacement hardware for my laptop, or upgrade laptops, it would be nice if I could move my applications to an area that is not dead, and use the laptop. Any suggestions on working around the global menu. It wouldn't be so annoying but the whole left inch of my screen is black, white, or rainbow stripes depending on the machines mood, so 'File' on every application is not visible. 

Thanks!

---

### Post by elsandkls on 2014-01-03
Ran:

# sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt
gtk appmenu-gtk3 appmenu-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'unity-gtk2-module' instead of 'appmenu-gtk'
Note, selecting 'unity-gtk3-module' instead of 'appmenu-gtk3'
unity-gtk2-module is already the newest version.
unity-gtk2-module set to manually installed.
unity-gtk3-module is already the newest version.
unity-gtk3-module set to manually installed.
The following NEW packages will be installed:
  appmenu-qt
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.3 kB of archives.
After this operation, 105 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main appmenu-qt i386 0.2.7daily13.05.02-0ubuntu1 [26.3 kB]
Fetched 26.3 kB in 0s (84.6 kB/s)     
Selecting previously unselected package appmenu-qt.
(Reading database ... 398012 files and directories currently installed.)
Unpacking appmenu-qt (from .../appmenu-qt_0.2.7daily13.05.02-0ubuntu1_i386.deb) ...
Setting up appmenu-qt (0.2.7daily13.05.02-0ubuntu1) ...
 


Then ran: 
sudo apt-get autoremove unity-gtk3-module unity-gtk2-module

Fixed it.

---

### Post by ibjsb4 on 2014-01-04
> My screen is in the process of dieing, and while I search for  replacement hardware for my laptop, or upgrade laptops, it would be nice  if I could move my applications to an area that is not dead, and use  the laptop. Any suggestions on working around the global menu. It  wouldn't be so annoying but the whole left inch of my screen is black,  white, or rainbow stripes depending on the machines mood, so 'File' on  every application is not visible.

Maybe you could just change screen resolution

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+resolution+screen+size&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+resolution+screen+size&sa=Search&cof=FORID:9)

---

### Post by deadflowr on 2014-01-04
This is available on the dev 14.04
[http://www.omgubuntu.co.uk/2013/11/unity-trusty-global-menu-switch?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2013/11/unity-trusty-global-menu-switch?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

---

### Post by elsandkls on 2014-01-14
Tried resizing before hunting for global menu solution, and it sort of works, but not really the greatest solution. 
Thanks for the link for 14.04 information. I'm looking forward to the next ubuntu version, and a newer laptop.

---

