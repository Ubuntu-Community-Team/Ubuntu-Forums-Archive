---
title: "After install no bottom panel"
date: 2010-11-08
forum: Desktop Environments
---

### Post by cygnis1 on 2010-11-08
Hi everyone,
I just did a fresh install of Ubuntu 10.10 and now I have no bottom panel.

After installation, I had a black screen with just the top panel and no icons.  I did manage to right click on the top panel and get the notification icons,and main menu on the panel.  But I still don't have the bottom panel. So when I open Firefox and Thunderbird there is no way to switch between the two windows.  In order to go from Thunderbird to Firefox I have to close out Thunderbird and vice versa.

I am running Ubuntu 10.10 with Gnome.  My theme is clear look, and it has the minimize maximize buttons on the right.  I don't know if that is what is causing my problem.  Please help.
Cygnis1

---

### Post by TheAnachron on 2010-11-08
Make a new clean install please, with these troubles after installation this system will not work for long.

---

### Post by wojox on 2010-11-08
Try resetting with these two commands


```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

---

### Post by cygnis1 on 2010-11-08
Thanks,
that worked.  Bless you.
Cygnis1

---

