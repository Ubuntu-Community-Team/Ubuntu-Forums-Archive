---
title: "Restore Ubuntu's 10.10 orignal panel"
date: 2011-03-16
forum: Desktop Environments
---

### Post by alab0 on 2011-03-16
Dear all...
I did remove my top ubuntu panel and I searched on this site [http://ubuntuforums.org/showthread.php?t=1652235]("http://ubuntuforums.org/showthread.php?t=1652235") but when I run the code on terminal the top panel appears without any icons :confused: plz help me to back the original panel setting.

---

### Post by Krytarik on 2011-03-16
Could you please provide a screenshot!?

EDIT: I forgot to mention, the command stated in the thread is generally correct.

---

### Post by utnubuuser on 2011-03-16
The commands for restoring the panels to "factory-new" settings:> cd /home/username
 then> rm -rf .gnome2 .gconf .gconfd .metacitythen> killall gnome-panelto restart the panels

Original thread:[http://ubuntuforums.org/showthread.php?t=1060406](http://ubuntuforums.org/showthread.php?t=1060406)

---

### Post by Krytarik on 2011-03-17
> **utnubuuser said:**
> The commands for restoring the panels to "factory-new" settings:
> cd /home/username
then
[QUOTE]rm -rf .gnome2 .gconf .gconfd .metacity
[/QUOTE]
This would *restore* almost your **entire Gnome environment** to *"factory-new" settings*! **Please don't do that!!** Unless you want to start over fresh of course.

@utnubuuser: I know, there are quite a lot of suggestions like this, but please check your own directories before echoing such a "solution"!

EDIT: Btw., the command mentioned by the OP is generally the correct command to reset just the panels.

---

### Post by wojox on 2011-03-17
To just reset the panels:

```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

---

