---
title: "Installed KDE throught apt: No suspend/hibernate?"
date: 2007-03-08
forum: Desktop Environments
---

### Post by bg1256 on 2007-03-08
Hey all,

I installed KDE over Gnome using apt-get,and I do not have the option to suspend or hibernate my computer. I would imagine there is a way to restore this, but I don't really know anything about KDE.

Any help is appreciated!

---

### Post by mmmpancakes on 2007-04-01
Bump. I'm having this same problem also. No options to suspend/hibernate on the logout menu. 

Help would be appreciated.

---

### Post by ronocdh on 2007-04-01
Don't know whether this is related, but I always add KDE by using ```
sudo **aptitude** install kubuntu-desktop
```I've heard that aptitude is just more reliable for big changes... I based my decision off the fact that aptitude yielded 212MB of things to grab, whereas apt-get only 187MB or something.

---

### Post by mmmpancakes on 2007-04-02
bump

---

### Post by ComplexNumber on 2007-04-02
> **bg1256 said:**
> Hey all,

I installed KDE over Gnome using apt-get,and I do not have the option to suspend or hibernate my computer. I would imagine there is a way to restore this, but I don't really know anything about KDE.

Any help is appreciated!
are you using GDM or KDM as your login manager?

---

### Post by mmmpancakes on 2007-04-02
I'm currently using KDM

---

### Post by mmmpancakes on 2007-04-02
Correction. I'm currently logging in with Gnome.

---

### Post by ComplexNumber on 2007-04-02
> **mmmpancakes said:**
> Correction. I'm currently logging in with Gnome.
meaning that you're using GDM? 

one thing that must be noticed is that the hibernate and restart feature in gnome is determined by the presence of GDM running. when my GDM wouldn't work properly, it had to use a different login manager. in addition, because GDM wasn't running, there was no option for hibernate and shutdown. i think its probably the same in KDE (ie KDM needs to be running).

---

### Post by mmmpancakes on 2007-04-02
That makes a tremendous amount of sense now that you've pointed that out. 

Would you be able to point me to a simple guide on how to install KDE over Gnome?

---

### Post by mmmpancakes on 2007-04-02
EDIT: I mean how to install KDM over GDM? 

(sorry - long day)

---

### Post by ComplexNumber on 2007-04-02
i can't remember exactly, but its something like this:

install kdm, then type in:
sudo dpkg-reconfigure kdm
however, when you instal kdm, it should ask you if it can configure it for you.



that should reconfigure it as your default login manager. 
maybe someone can correct me on this.

---

### Post by mmmpancakes on 2007-04-02
Excellent. That worked. Now KDE/KDM fully installed, but still no suspend/hibernate options on shutdown.

---

### Post by ComplexNumber on 2007-04-02
> **mmmpancakes said:**
> Excellent. That worked. Now KDE/KDM fully installed, but still no suspend/hibernate options on shutdown.
logout then login again. that should get kdm running, so the hibernate feature etc should then be present. 
instead of logging out, reboot instead....just to be on the sure side.

---

### Post by bcrowell on 2007-04-02
Make sure you have S3 sleep mode enabled in BIOS, not just S1. If you don't have S3 enabled, GNOME won't show you the suspend option.

Another option would be just to do the following from the command line:

sudo /etc/acpi/hibernate.sh

sudo /etc/acpi/sleep.sh force

---

