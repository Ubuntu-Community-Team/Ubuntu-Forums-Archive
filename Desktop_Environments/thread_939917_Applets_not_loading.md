---
title: "Applets not loading"
date: 2008-10-06
forum: Desktop Environments
---

### Post by JacobOfLinux on 2008-10-06
Hi, recently my applets have been not loading (trash, battery indicator etc.)
I get this error (the applet name will change for each applet) when I login:
```
The panel encountered a problem while loading "OAFIID:GNOME_BattstatApplet".
Do you want to delete the applet from your configuration?

``` 
I'm sort of lost on this one.  :( :confused:

---

### Post by JacobOfLinux on 2008-10-07
Never mind, I fixed this by doing the following
sudo apt-get purge gnome-desktop-data
sudo apt-get install ubuntu-desktop
:)

---

### Post by archangel74 on 2008-11-21
> **JacobOfLinux said:**
> Never mind, I fixed this by doing the following
sudo apt-get purge gnome-desktop-data
sudo apt-get install ubuntu-desktop
:)
Yes, this does work indeed.  I lost my ALL applets after running a e2fsck on partition 2 from partition 1. Not sure why but thanks for the advice.  I was worried.

---

### Post by roscog4 on 2010-02-02
I was having a similar problem with applets so I followed your suggested commands. Evey thing purged just great but unfortunately the install command said it couldn't find everything that was needed to successfully complete it. After about 10 unsuccessful tries I restarted the computer and now I can not log in. It simply flashes a quick white screen the comes back to the log in page. I noticed that the sessions window has dissappeared from my log in screen as well. Any help would be much appreciated. 

FYI: I am new to Linux

---

