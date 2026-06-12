---
title: "Gnome System Monitor"
date: 2008-06-13
forum: Desktop Environments
---

### Post by soccerboy on 2008-06-13
Has anyone else noticed that the system monitor in Gnome takes 10-20% processor time continuously when it is turned on?  I think that is too much.  I remember, Microsoft was able to implement one using only 1-2% on the my same machine, from my Windows days.  What do you think?

---

### Post by sdennie on 2008-06-13
Yes.  It's a known bug.  It's listed in the sticky at the top of the General Help forum: [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by diaa on 2008-06-13
> **soccerboy said:**
> Has anyone else noticed that the system monitor in Gnome takes 10-20% processor time continuously when it is turned on?  I think that is too much.  I remember, Microsoft was able to implement one using only 1-2% on the my same machine, from my Windows days.  What do you think?

Yes I did, that's a bitter fact of ... GNOME, I recommend using a more efficient process manager such as htop(terminal) or qps if you prefer GUIs both use less than 1% of CPU time until they improve gnome apps.

btw, I just switched to KDE so may be you should give it a try :)

EDIT:
There are several alternative process managers available in case you want a variety to choose from
CLI(Command-Line Interface):
top
atop
htop

GUI:
gps
qps
xfce4-taskmanager

IMHO htop is the best of CLI and qps and xfce4-taskmanager is the best of GUI but your mileage may vary :)

---

### Post by soccerboy on 2008-06-13
I don't mind using GNOME.  KDE gives me too much of a Windows feel and I strive for an Ubuntu feel.  My brother uses KDE though, he likes it.  I rarely use system-monitor because there is rarely a need.  Usually everything works as expected.  It is just frustrating when you are trying to find which process is using all your resource and it gets changed because you opened monitor.  the application showing you the resource usage is now the biggest resource hog.

---

### Post by chris4585 on 2008-10-10
Thank you! qps is my new favorite system monitor

---

