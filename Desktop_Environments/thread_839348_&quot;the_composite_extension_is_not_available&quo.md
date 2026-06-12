---
title: "&quot;the composite extension is not available&quot;"
date: 2008-06-24
forum: Desktop Environments
---

### Post by Afkpuz on 2008-06-24
So long story short, I downgraded from hardy back to gutsy.  Well, I've ran gutsy before and followed the same steps I always took to get desktop effects working.  Install restricted driver, than enable effects.  Used to work in the past on clean installs, but not this one.  When I try to enable effects, I get the message "the composite extension is not available".  


How to fix?  why did it decide to do this on this installation when I've done it on a dozen installs without getting this problem?

---

### Post by x1a4 on 2008-06-24
I'm not 100% on this, but it seems like Xorg doesn't have the Composite extension enabled.  Edit your /etc/X11/xorg.conf file and append the following to it.
```

Section "Extensions"
     Option     "Composite" "Enable"
EndSection

```
Restart GDM when done.
```
sudo /etc/init.d/gdm restart
```

---

