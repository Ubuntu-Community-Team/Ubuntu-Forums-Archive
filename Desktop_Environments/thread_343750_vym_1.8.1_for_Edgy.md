---
title: "vym 1.8.1 for Edgy"
date: 2007-01-21
forum: Desktop Environments
---

### Post by lduperval on 2007-01-21
Hi,

Does anyone know if a version of Vym 1.8.1 exist for Edgy somewhere? The current version in the various repositories is 1.7.4. Since I don't do much development or source compilations, I would rather not have to compile it manually and get all the KDE/QT/??? development tools installed.

Any ideas?

Thanks,

L

---

### Post by MisterT2 on 2007-02-17
:?: 
Any idea ?
Thanks

---

### Post by pay on 2007-02-17
```
sudo aptitude install alien
wget http://downloads.sourceforge.net/vym/vym-1.8.1-suse-10.1-i586.rpm
sudo alien -i vym-1.8.1-suse-10.1-i586.rpm
```

---

### Post by deltoya on 2007-02-17
You may try the debian package [here]("http://packages.debian.org/testing/kde/vym"), which dependences are solved in Edgy.
Feisty also has 1.8.1, but depends on a higher version of libc6 than the available for Edgy. Anyway, Feisty is almost here (aprox 6 weeks), if you can wait...

---

### Post by MisterT2 on 2007-02-17
> **pay said:**
> ```
sudo aptitude install alien
wget http://downloads.sourceforge.net/vym/vym-1.8.1-suse-10.1-i586.rpm
sudo alien -i vym-1.8.1-suse-10.1-i586.rpm
```
Thanks a lot for this incredibly fast answer !
That's not what I was thinking of, but it works pretty fine....
Good... :)

---

### Post by pay on 2007-02-17
On the official website it says to install alien and then convert an rpm. It would probably be better if you compiled the source code though.

---

### Post by zhinker on 2007-05-29
> **pay said:**
> On the official website it says to install alien and then convert an rpm. It would probably be better if you compiled the source code though.
Could you explain how to do that?  I tried to work through it but I couldn't figure it out.

---

