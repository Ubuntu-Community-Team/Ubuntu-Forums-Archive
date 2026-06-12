---
title: "xubuntu-desktop and XGL; how?"
date: 2006-12-16
forum: Desktop Environments
---

### Post by sarikan on 2006-12-16
Hi there,
I have given a try to xubuntu-desktop package in drapper drake and I am very happy with it, it is really snappy, but having XGL on top of it would be really cool. 
At the moment I have XGL working fine with gnome, but I have failed to find a link for xubuntu-desktop package and xgl integration.
Is it possible to have such a combination? 
Regards
Seref Arikan

---

### Post by Rmorris84 on 2006-12-16
I also just moved to the xubuntu desktop as of yesterday... and I also had beryl working in ubuntu(gnome). Surprisingly its easy. I did a lil searching around and it seems the window manager in xfce doesnt allow beryl to work properly.  And someone suggested either removing or making it where window manager doesnt start up. So what i suggest u try is

```
killall xfwm4
```

i dont know what version u are using but thats my window manger on dapper in the xfce desktop. and then my beryl loaded up when i selected it as my window manager from the tray icon. 

Hope that helps... I didnt remove it completely (yet) all i did was kill it.... I never reboot ( i love linux :-D ) but if that helps you and beryl works, then u could remove the window manager.

---

### Post by sarikan on 2006-12-17
Hi, 
thanks a lot!!! 

killall xfwm4

did the trick. Using compiz at the moment, and I'm very happy with the results so far.

Regards

Seref Arikan

---

