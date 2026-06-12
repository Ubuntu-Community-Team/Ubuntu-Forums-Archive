---
title: "Packages not updated by apt-get upgrade"
date: 2009-01-31
forum: General Help
---

### Post by orangey on 2009-01-31
Got a general question that's been bugging me for a while.  I notice that when I use "apt-get -u upgrade" to update my system, some major components are always kept back, i.e. linux-headers-generic, linux-image-generic, etc.  But they do get updated if I use System-Administration->Update Manager, they do get updated.  Why is that.  Also, what if I am using ubuntu server and don't have gnome desktop?

---

### Post by Boomhauer on 2009-01-31
will ```
# aptitude upgrade
``` install them?

---

### Post by orangey on 2009-01-31
Tried aptitude too.  Specifically, "aptitude safe-upgrade".  Same results.  Oh btw, my server is running gutsy 7.10

---

### Post by p_quarles on 2009-02-01
The "upgrade" argument won't upgrade any packages that change the dependency tree. To attempt a "smart" upgrade to the newest version of every package, you need to run:
```
sudo apt-get dist-upgrade
```

---

### Post by orangey on 2009-02-01
Ah that was it.  Thanks p_quarles.

---

