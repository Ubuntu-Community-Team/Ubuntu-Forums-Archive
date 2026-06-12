---
title: "View windows shares on e17"
date: 2008-10-10
forum: Desktop Environments
---

### Post by Maverick_Hunter on 2008-10-10
Hi, i have been using ubuntu (and xubuntu) for a while now, and i recently made the jump to e17, i want to keep this as my main DE but i want to know, how do i view windows shares?

Thanks in advance!

---

### Post by sokopok on 2008-10-10
windows file and printer sharing is handled by samba, so if it isn't already installed, install samba. then from the file manager (dolphin, nautilus) go to network and you windows shares should be visible there

---

### Post by Maverick_Hunter on 2008-10-11
Samba is installed, but in Thundar (no nautilus in e17, if i start it it bugs up the system) there is no Network Servers tab

---

### Post by lwb1086y on 2008-10-11
***[size=2]Nice topic. A+++++++[/size][size=2][/size]***------------------------------------------------------------------------------------------------------------------------------[img]http://www.qzone.la/img/userup/0808/2GU2563439.jpg[/img]Welcome to our wow power leveling site:cheap [AOC Power Leveling](http://www.toppowerlevel.net/powerlist.php?fid=2960),buy [MapleStory Mesos](http://www.toppowerlevel.net/gamelist.php?fid=1468),buy [RuneScape Gold](http://www.toppowerlevel.net/gamelist.php?fid=4011),[WARHAMMER ONLINE GOLD](http://www.toppowerlevel.net/gamelist.php?fid=3966),[SilkRoad Gold](http://www.toppowerlevel.net/gamelist.php?fid=4013)

---

### Post by worldwithoutgurus on 2008-10-11
Use this command:

nautilus --no-desktop

---

### Post by bones12 on 2010-01-22
For anyone who is looking for an answer here. I have a temporary fix for  getting to smb or windows share after starting an E17 session. Open a terminal window and remount using

sudo mount -a

I didn't want to load the gnome-desktop in order to get nautilus running as one of the post suggested. I am running on an xfce4, Xubuntu 9.10 system and didn't already have nautilus installed.

---

