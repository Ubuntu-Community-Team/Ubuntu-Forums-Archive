---
title: "Latest Debian with Net Install"
date: 2008-12-28
forum: Debian
---

### Post by Istonian on 2008-12-28
I am going to install Debian on my computer. I want the latest version of Debian whether it be testing or sid or whatever. What would I have to download to have the latest Debian build using a net install?

---

### Post by SPr on 2008-12-29
[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

Edit /etc/apt/sources.list to point to either Lenny or Testing depending on what you want.

---

### Post by kerry_s on 2008-12-29
> **Istonian said:**
> I am going to install Debian on my computer. I want the latest version of Debian whether it be testing or sid or whatever. What would I have to download to have the latest Debian build using a net install?

testing is the most stable and usable, you just need this:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

---

### Post by Bachstelze on 2008-12-29
> **kerry_s said:**
> testing is the most stable and usable, you just need this:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

He asked for the latest, and that is Sid (unstable), which is just as good and usable as Lenny (and sometimes even better, since security updates get into it much faster).

---

### Post by blackgr on 2008-12-29
> **HymnToLife said:**
> He asked for the latest, and that is Sid (unstable), which is just as good and usable as Lenny (and sometimes even better, since security updates get into it much faster).

Unstable version of debian has no repository for security updates. The only available repositories for security updates are for stable and testing version.

---

### Post by Bachstelze on 2008-12-29
> **blackgr said:**
> Unstable version of debian has no repository for security updates. The only available repositories for security updates are for stable and testing version.

I know that, thank you very much. The security updates in Sid are merged in the main repository, like all other updates.

---

### Post by Istonian on 2008-12-29
Ok, I have a couple of questions. What is the difference between the business card image and the net install image?

Also, can I just change the repositories after installation?

---

### Post by Bachstelze on 2008-12-29
> **Istonian said:**
> Ok, I have a couple of questions. What is the difference between the business card image and the net install image?

[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

> **What is the difference between the netinst and the business card images?** The netinst image contains the installer and the base system. It will allow you to install a very basic system from the CD; any other packages you might want to install have to be downloaded from the internet. 
 The business card image is smaller than the netinst image to fit on business-card sized cds. It does not contain the base system, but only the installer: even the base packages need to be downloaded from the net. 
 If you're in doubt which image to use, use the netinst image.


> Also, can I just change the repositories after installation?

Yes, if you want to upgrade (i.e. from stable to testing or unstable, or from testing to unstable). Downgrading, is possible too but not as straightforward, and can cause a few headaches along the way.

---

### Post by Istonian on 2008-12-29
Thanks for all the help. I might have a few more questions as I go along. As of now I have a working system!

EDIT: How do I enable the non-free unnstable repos?

---

### Post by Bachstelze on 2008-12-29
Just add it to your [font="monospace"]sources.list[/font]. If you want to use Sid, it should look like this:

```
deb http://ftp.fr.debian.org/debian/ sid main contrib non-free
deb-src http://ftp.fr.debian.org/debian/ sid main contrib non-free
```

Of course with a different mirror. ;)

---

