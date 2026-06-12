---
title: "awn prefences?"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by luckyd on 2007-07-30
I just installed a new version of the awn svn .deb, and now when i right click for preferences and click nothing comes up. the same is true for configure applets and launchers. What can i do?

---

### Post by luckyd on 2007-07-30
Also, i cant even change the applet setting in gconf, because they are not there anymore.

---

### Post by Espreon on 2007-07-30
Try COMPLETELY uninstalling it (purge it) and reinstalling AWN. I have the latest SVN version and I can configure it fine.

---

### Post by walkerk on 2007-07-30
> **Espreon said:**
> Try COMPLETELY uninstalling it (purge it) and reinstalling AWN. I have the latest SVN version and I can configure it fine.

yep.. you need to ensure that everything awn related is gone before installing the new svn .deb.

---

### Post by luckyd on 2007-07-30
What is everything, purging from synaptic doesn't work, so there have got to be some files left behind...

---

### Post by luckyd on 2007-07-30
bump

---

### Post by forrestcupp on 2007-08-06
I had the same problem.  Run gconf-editor NOT as root.  Just run gconf-editor without the sudo and you should have entries.

---

### Post by Churnd on 2007-10-21
I had a similar problem too... installed a theme I didn't like and tried to remove it at no avail.  Tried apt-get remove and purge several times with reboot which didn't work.

This worked:

From Terminal, type:
```
gconftool-2 --recursive-unset /apps/avant-window-navigator
```

This resets AWN back to it's original state.

---

