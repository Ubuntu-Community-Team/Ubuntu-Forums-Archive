---
title: "this sucks :p"
date: 2007-07-07
forum: Desktop Environments
---

### Post by x1a4 on 2007-07-07
kdm ignored orders from X.  
gdm didn't

How do I start multiple kdm sessions?  Thank You.  X is configured correctly.  GDM knew what to do.  In case anybody missed it, I just switched from GDM to kdm.

---

### Post by aysiu on 2007-07-07
Well, if GDM is working for you, is there any reason you need KDM?

---

### Post by russianpirate on 2007-07-08
perhaps he decided to use kde? kdm is better integrated with kde

---

### Post by aysiu on 2007-07-08
You can easily use GDM with KDE. I still don't see a problem here.

---

### Post by x1a4 on 2007-07-08
> **aysiu said:**
> Well, if GDM is working for you, is there any reason you need KDM?

for fun

---

### Post by x1a4 on 2007-07-08
> **russianpirate said:**
> perhaps he decided to use kde? kdm is better integrated with kde

Yes.  I installed kde-core.  Though my favourite interface at the moment is Sawfish, augmented with FluxBox and GTK features.

---

### Post by aysiu on 2007-07-08
Can you describe more exactly what the problem is?

For example, have you tried this? Control-Alt-F1 ```
sudo /etc/init.d/gdm stop
sudo nano -B /etc/X11/default-display-manager
``` Change /usr/sbin/gdm to /usr/bin/kdm and then ```
sudo /etc/init.d/kdm start
``` If that doesn't work, what's the error message?

---

