---
title: "Gnome panel problems"
date: 2008-11-01
forum: Desktop Environments
---

### Post by heiowge on 2008-11-01
I installed Intrepid when it came out and lost my Gnome panel.  It was there until I rebooted, then it went.  I reinstalled the panel, and it was fine.  Now this morning my shutdown button etc. has vanished.

Is this a normal problem with Intrepid?

---

### Post by heiowge on 2008-11-01
...and I don't seem to be able to get it back :confused:

---

### Post by heiowge on 2008-11-04
My user switcher has gone from Add to panel.  I suspect that has an impact.  Also, my taskbars have disappeared twice now.

---

### Post by heiowge on 2008-11-05
bump

---

### Post by ZankerH on 2008-11-05
Try manually purging the panel config files in ~/.gconf/apps/panel. If you're using the old config files from 8.04.1, this could be a compatibility issue and starting out new may be the easiest solution.

---

### Post by heiowge on 2008-11-05
Sounds like you know what you're talking about.  Any chance of walking me through it?

Cheers.

---

### Post by ZankerH on 2008-11-05
> **heiowge said:**
> Sounds like you know what you're talking about.  Any chance of walking me through it?

Cheers.

Delete the /home/yourusername/.gconf/panel directory. You'll need to select "show hidden files" under the view menu to see it in nautilus. If you're afraid of messing things up worse than they are right now, back it up first.

---

### Post by heiowge on 2008-11-09
Done.  No joy though.:confused:

---

### Post by heiowge on 2008-11-12
bump

---

### Post by bgs100 on 2008-11-12
Hit Alt+F2 (or terminal) and put in:
```
gnome-panel
```
then press "Run" (or hit enter if using terminal)

---

