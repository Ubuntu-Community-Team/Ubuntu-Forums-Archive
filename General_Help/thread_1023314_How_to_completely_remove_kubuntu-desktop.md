---
title: "How to completely remove kubuntu-desktop?"
date: 2008-12-27
forum: General Help
---

### Post by acablue on 2008-12-27
I installed the kubuntu-desktop package to try out KDE 4.1, but I decided I'd rather stick with GNOME. However, when I removed the kubuntu-desktop package, all of KDE's dependencies and applications remained installed. How do I completely remove them without removing the system files that GNOME relies on?

---

### Post by MarblePanther on 2008-12-27
Open synaptic and look for the category in status called installed(autoremovable).

highlight everything in there and right click complete removal

should take care of it

Make sure you are in the auto-removable category--important!

Also make sure there is nothing in there you may want (nothing will be necessary that is in that section)

---

### Post by jorj82 on 2008-12-27
Check this out [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by acablue on 2008-12-27
This is the error message I get when I run that command:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by stoneage on 2008-12-27
Do you have Synaptic open?

---

### Post by acablue on 2008-12-27
Whoops never mind, I found the solution in another thread. 

jorj82's solution worked perfectly.

---

