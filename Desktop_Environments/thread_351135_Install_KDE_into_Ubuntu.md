---
title: "Install KDE into Ubuntu"
date: 2007-02-01
forum: Desktop Environments
---

### Post by uk_falang on 2007-02-01
Hi
I have just installed Ubuntu.

I want to use KDE as well as Gnome

My Ubuntu machine does not have internet yet - so can i download the files and then install from the cdrom?

And then how will i change from gnome to kde?

Thanks (ps New to Linux

---

### Post by glabouni on 2007-02-01
for a basic kde:
```
sudo apt-get install kdebase
```
for a full kubuntu:
```
sudo apt-get install kubuntu-desktop
```

then when you are at login screen, before login, search the session button/menu and select the session you wanna log in kde or gnome.

---

### Post by aysiu on 2007-02-01
If uk_falang is on Dapper, *apt-get*ting KDE could be a bad, bad idea, especially if she or he wants to remove KDE later.

Follow these instructions instead:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

