---
title: "please step by step using terminal for Desktops removal"
date: 2013-11-13
forum: Desktop Environments
---

### Post by fatharraxman on 2013-11-13
when open my Laptop at the greeting level I have these Desktops environments:
GNOME/Openbox
LX Games
LXDE
Lubuntu
Lubuntu Netbook
Lubuntu Nexus7 session
Lubuntu Qt session
etc 
I want to remove them all, leaving only Default desktop environment, I tried and tried using terminal where it tells me it is removed but reboot to face them again stick there like a virus lol.

---

### Post by Bucky Ball on 2013-11-13
*Thread moved to **Desktop Environments**.*

Try removing them via Synaptics or Software Centre. I know this will work for lxde. You'll have to search for the others.

---

### Post by Dennis N on 2013-11-13
Which one is the default? This is an alphabetical list.

Easier said than done, at least in some cases here. For example, most if not all Lubuntu-specific packages come from installing **lubuntu-desktop** package. Removing lubuntu-desktop doesn't remove Lubuntu or any of its components, since lubuntu-desktop is just a metapackage.

Some packages of lubuntu-desktop can be removed individually, of course. But others may be used by other desktops or are dependencies of other applications you want to keep and can't be removed.

---

### Post by steeldriver on 2013-11-13
If you're not running out of disk space and simply want to prevent the alternate desktops from being listed by the session chooser, you could just rename the .desktop files in /usr/share/xsessions/ e.g.

```
sudo mv /usr/share/xsessions/LXDE.desktop /usr/share/xsessions/LXDE.desktop.ignore
```

This will likely be safer than trying to remove the desktop metapackages themselves

---

### Post by fatharraxman on 2013-11-13
> **steeldriver said:**
> If you're not running out of disk space and simply want to prevent the alternate desktops from being listed by the session chooser, you could just rename the .desktop files in /usr/share/xsessions/ e.g.

```
sudo mv /usr/share/xsessions/LXDE.desktop /usr/share/xsessions/LXDE.desktop.ignore
```

This will likely be safer than trying to remove the desktop metapackages themselves

Yup this surprisingly hided lxde but the others still there besides, the synaptic is not launching 
Thank you guys

---

### Post by Bucky Ball on 2013-11-13
> **fatharraxman said:**
> I wounder if you can answer two more questions or should I start new thread for hem?
How can I make the login page ask me for my password 
and how can I stop this message: type you password for keyring which show up after every login


Yes, post new threads. Please stick to one support question per thread or it just gets confusing. Three here will become totally confusing. Post in appropriate sections with a descriptive title and all info of what you've done and what is happening. Thanks.

---

