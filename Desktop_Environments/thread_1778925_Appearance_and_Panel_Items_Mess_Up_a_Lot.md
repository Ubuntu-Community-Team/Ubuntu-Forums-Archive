---
title: "Appearance and Panel Items Mess Up a Lot"
date: 2011-06-09
forum: Desktop Environments
---

### Post by duranl on 2011-06-09
Hello,

About 90% of the time I log on to Ubuntu 11.04 Gnome, something is wrong with the environment: either a panel item is missing or the entire theme is changed.  Also, sometimes I have to click THREE times on the Ubuntu symbol on the upper left to get my menu items to appear.  This only happens with the main user (the one that was first made through the installation).  The other two users have not had any problems so far.

Is there anyway I stop these issues from arising?

Thanks in advance! :p

---

### Post by searchfgold6789 on 2011-06-09
Well, the only thing I can personally think of is that it may have something to do with the graphics driver you have installed; there could be some problems with permissions. That could jog your memory about something you did with special graphics drivers, but it could be something else too... like having to reconfigure xorg or gdm ('sudo dpkg-reconfigure -phigh xserver-xorg' or 'sudo dpkg-reconfigure -phigh gdm') although I would hate to see you do that and have all of your settings mixed up and be unable to get to a desktop.
Sorry if my answer seems vague, but I thought I might be able to at least make a suggestion :)
 - search

---

