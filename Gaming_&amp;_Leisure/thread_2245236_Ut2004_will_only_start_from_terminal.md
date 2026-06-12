---
title: "Ut2004 will only start from terminal"
date: 2014-09-22
forum: Gaming &amp; Leisure
---

### Post by Alasta on 2014-09-22
Good morning 

I have a working Ut2004 linux install on ubuntu 14.04. This is a new install on a dual core pentuim with 6gb of ram and a nvidi  GF119 [GeForce GT 610] graphics card. This game will not start by double clicking in nautilus . if you navigate to the folder using the terminal with /usr/local/games/ut2004 and type ut2004 it works just fine . My end goal would be a launcer in the dash : ) 


KIndest regards

Alastair

---

### Post by R33D3M33R on 2014-09-22
Try creating a .desktop file with the help of this guide: [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)
You might need to add Path=/path/to/ut2004/folder/ below the Exec line.

---

### Post by Alasta on 2014-09-22
Many Many thanks . Worked a charm 

SOLVED

---

