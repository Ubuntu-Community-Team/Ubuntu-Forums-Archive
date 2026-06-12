---
title: "notification area becomes ugly"
date: 2011-02-19
forum: Desktop Environments
---

### Post by obirama on 2011-02-19
hi everyone

several days ago i installed kubuntu-desktop package in my ubuntu 10.04. everything works fine until i login back to gnome. my notification area appeared as in kde. it is fine for me but some notification popup become ugly and look corrupted. any idea to get back to default notification in gnome? screenshot attached

---

### Post by obirama on 2011-02-20
just an update,the problem is solved now. just do 
```
sudo dpkg-reconfigure notification-daemon notify-osd
```
or
```
sudo dpkg-reconfigure notification-daemon notify-osd
```
sorry i didnt know which command that worked.i just ran both command and reboot.
thanks.

---

