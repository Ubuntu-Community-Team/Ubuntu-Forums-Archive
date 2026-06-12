---
title: "the KDM theme [Resolved]"
date: 2007-01-01
forum: Desktop Environments
---

### Post by Absurd on 2007-01-01
How do I change the KDM theme in Kubuntu? 

I already tried going to Kmenu->Advanced->Login Manager and changing the settings there, but that doesn't seem to do anything.

---

### Post by aysiu on 2007-01-01
Extract it to /usr/share/kdm/themes and then edit /etc/kde3/kdm/kdmrc and make sure it's using your new theme instead of /usr/share/kdm/themes/kubuntu

---

### Post by Absurd on 2007-01-01
extract what? a tarball containing a theme?

---

### Post by aysiu on 2007-01-01
> **Absurd said:**
> extract what? a tarball containing a theme?
Yes, extract the theme .tar.gz file.

A new folder should appear, and that should be moved to /usr/share/kdm/themes/

---

### Post by Absurd on 2007-01-01
thanks

btw, the directory is /usr/share/apps/kdm/themes/

---

### Post by aysiu on 2007-01-01
Thanks for the correction. I was going off memory. So it worked?

---

### Post by Absurd on 2007-01-01
Yes, it worked. :D Thanks

---

