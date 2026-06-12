---
title: "Can't launch ``gdmsetup'' [RESOLVED]"
date: 2006-10-14
forum: Desktop Environments
---

### Post by ansi on 2006-10-14
[~] sudo gdmsetup
```
Could not access GDM configuration file.
```

[~] ls -l /etc/X11/xorg.conf
-rw-r--r-- 1 root root 4279 2006-10-07 09:23 /etc/X11/xorg.conf



It is a first launching of this utility. How I can execute this program && what is the problem? Thank you.

**Ubuntu 6.06.1LTS with fresh updates.**

---

### Post by aysiu on 2006-10-14
This may not be the problem, but the actual command you should be using is ```
gksudo gdmsetup
```

---

### Post by ansi on 2006-10-14
> **aysiu said:**
> This may not be the problem, but the actual command you should be using is ```
gksudo gdmsetup
```

It is no matter, imho. I have a habit to use native ``sudo'' command instead of wrappers :).

[~] gksudo gdmsetup
(gdmsetup:7189)Could not access GDM configuration file.

---

### Post by aysiu on 2006-10-14
When I look for *gdm.conf*, this is what I get: ```
**locate gdm.conf**
/var/lib/dpkg/info/gdm.conffiles
/var/lib/dpkg/info/gdm.config
/etc/gdm/factory-gdm.conf
/etc/gdm/gdm.conf
/etc/gdm/gdm.conf-custom
``` Do you have all those files?

---

### Post by ansi on 2006-10-14
> **aysiu said:**
> When I look for *gdm.conf*, this is what I get: ```
**locate gdm.conf**
/var/lib/dpkg/info/gdm.conffiles
/var/lib/dpkg/info/gdm.config
/etc/gdm/factory-gdm.conf
/etc/gdm/gdm.conf
/etc/gdm/gdm.conf-custom
``` Do you have all those files?

Of course.
[~] locate gdm.conf
```

/etc/gdm/gdm.conf
/etc/gdm/gdm.conf-custom
/etc/gdm/factory-gdm.conf
/etc/gdm/gdm.conf.old
/var/lib/dpkg/info/gdm.config
/var/lib/dpkg/info/gdm.conffiles
```

.old -- it is a backup copy of gdm.conf.

---

### Post by aysiu on 2006-10-14
That's odd. Everything's there.

What happens if you use gdm.conf.old? ```
sudo mv /etc/gdm.conf /etc/gdm.conf.new
sudo mv /etc/gdm.conf.old /etc/gdm.conf
``` By the way, if you want a functioning login screen manager in the meantime, you can use KDM: ```
sudo aptitude update
sudo aptitude install kdm
sudo /etc/init.d/kdm start
```

---

### Post by ansi on 2006-10-14
> **aysiu said:**
> That's odd. Everything's there.

What happens if you use gdm.conf.old?

No changes are. I have tried to reconfigure ``gdm'' package, but gdm.conf wasn't replaced or touched :mad:.

```
 By the way, if you want a functioning login screen manager in the meantime, you can use KDM: 
```
There is no doubt, that it is a good exit from this problem. But I:
 - Want to understand and solve this problem
 - I don't want to install libraries related with KDE & Co. I'm prefer, at present, use GNOME libraries only ;).

---

### Post by aysiu on 2006-10-14
I just wanted to make sure you weren't login screen-less while trying to figure out the problem.

---

### Post by Aurelius on 2006-10-14
> **ansi said:**
> [~] sudo gdmsetup
```
Could not access GDM configuration file.
```

[~] ls -l /etc/X11/xorg.conf
-rw-r--r-- 1 root root 4279 2006-10-07 09:23 /etc/X11/xorg.conf



It is a first launching of this utility. How I can execute this program && what is the problem? Thank you.

**Ubuntu 6.06.1LTS with fresh updates.**

This probably won't help you much, but for what it's worth I had the exact same problem last week. GDM worked fine, but I was unable to use gdmsetup to change the options. I posted a thread about it, but never got any responses. I just saw this thread and decided to try it again, and amazingly enough it worked.

I didn't really do anything to fix it - it just started working again on its own.

---

### Post by ansi on 2006-10-15
So, I couldn't find the source of problem, and have applied f windowz-style problem solving method: I have removed package ``gdm'' with purge of cfg's, and re-installed it afresh.

Question is closed. Thank's to all.

---

