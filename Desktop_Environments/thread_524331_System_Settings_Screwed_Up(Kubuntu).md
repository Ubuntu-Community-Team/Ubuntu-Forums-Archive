---
title: "System Settings Screwed Up(Kubuntu)"
date: 2007-08-13
forum: Desktop Environments
---

### Post by evri2 on 2007-08-13
Hello guys.I have a problem.I think it happened after installation of KDE 3.5.7. Look at the picture pls.    [http://img58.imageshack.us/img58/8164/snapshoat1dn9.jpg](http://img58.imageshack.us/img58/8164/snapshoat1dn9.jpg)  Anyone has seen sth like this?And the system settings button in the KMENU doesn't work and it gives SIGSEGV(11) error.

---

### Post by Austin_KW on 2007-08-18
> **evri2 said:**
> Hello guys.I have a problem.I think it happened after installation of KDE 3.5.7. Look at the picture pls.    [http://img58.imageshack.us/img58/8164/snapshoat1dn9.jpg](http://img58.imageshack.us/img58/8164/snapshoat1dn9.jpg)  Anyone has seen sth like this?And the system settings button in the KMENU doesn't work and it gives SIGSEGV(11) error.

I tripped over this when installing the gutsy kernel on feisty. Neither kcontrol or system settings will work. You need to fix the menus as follows
```

sudo mkdir /etc/xdg/menus/applications-merged

sudo cp /etc/xdg/menus/kde-applications-merged/kde-essential.menu /etc/xdg/menus/applications-merged/kde-essential.menu

sudo cp /etc/xdg/menus/kde-applications-merged/system-settings-merge.menu /etc/xdg/menus/applications-merged/system-settings-merge.menu

```
Or you could make links to the appropriate files, but the above should work.

---

