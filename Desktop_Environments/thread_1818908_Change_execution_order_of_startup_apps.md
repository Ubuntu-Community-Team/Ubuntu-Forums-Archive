---
title: "Change execution order of startup apps"
date: 2011-08-05
forum: Desktop Environments
---

### Post by mrengert on 2011-08-05
How do you change the order of execution of gnome startup apps?

(System - Preferences - Startup Applications) does not seem to have any way to do it.

I saw an archived post ([http://ubuntuforums.org/showthread.php?t=659420](http://ubuntuforums.org/showthread.php?t=659420)) which offered a couple of ideas... (1) mucking around with /etc/rc2.d/ -- but that seems to be only system-level apps, not user apps; or (2) going to (System - Preferences - Sessions) and mucking around in there -- but I don't seem to have that menu on my system (10.04 LTS running as a guest in vmware player 3.1)

I just want vmware-user to run before my gnome-terminals so that the desktop is resized before the terminals run.

---

### Post by wildmanne39 on 2011-08-05
Hi, make a sleep script for gnome-terminals it will look something like this.
> conky -p 40 -c ~/.conkyrc &
conky -p 40 -c ~/.conkyrc1 &
conky -p 40 -c ~/.conkyrc2 &
exit
of course this is for three conky's to sleep you will only need one.

I am not an expert on this.

---

