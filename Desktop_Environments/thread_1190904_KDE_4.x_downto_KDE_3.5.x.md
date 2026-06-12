---
title: "KDE 4.x downto KDE 3.5.x"
date: 2009-06-18
forum: Desktop Environments
---

### Post by JustinHD on 2009-06-18
Kmix in KDE 4.x is missing something vital to my sound system, and i found out that KDE 3.5.x has that vital component.

Solution 1 : How do i downgrade to 3.5.x from KDE 4.x?

Solution 2 : Or how do i bring the Kmix from 3.5.x to 4.x?

Im currently using Kubuntu 9.04

---

### Post by JustinHD on 2009-06-18
Bump

---

### Post by Zorael on 2009-06-18
No sense bumping after only two hours.

Without going into why you want the 3.5.x one, you can probably download the old Hardy kmix package and try to install that one. No guarantees as to if it'll *work* or even install.

[http://packages.ubuntu.com/hardy/kmix](http://packages.ubuntu.com/hardy/kmix)

---

### Post by JustinHD on 2009-06-18
Because, Dear Zorael, Kmix in KDE 4.x doesn't have the tab to enable channel swapping such as Center with LFE. Because my center/lfe channels are swapped in KDE 4.x
i.e. when i turn down the volume for center my subwoofer volume turns down => the outputs are swapped so i need to swap them back.

Edit: Kmix from Hardy won't install. Unknown Error.

---

### Post by Clorow on 2009-06-18
Press Alt+F2 and type in:
```
kdesudo kate /etc/apt/sources.list
```Add these four lines to the end of the file:
```
deb [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) intrepid main
```then save and close the text editor. After that, type into a terminal:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 44869960 && sudo apt-get update && sudo apt-get install kmix-kde3
```**Or** if you want to downgrade to KDE 3.5, then type into a terminal:
```
sudo apt-get install kubuntu-desktop-kde3
``` and next time you reboot or log out, change the session to KDE 3 instead of KDE 4.

---

### Post by JustinHD on 2009-06-19
Thanks Clorow, figured that out last night but KDE 3 didn't help me with my problem....so i did a fresh reinstall of Kubuntu.

---

