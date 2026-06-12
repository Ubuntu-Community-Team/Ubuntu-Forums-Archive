---
title: "Screenlets"
date: 2009-09-22
forum: Desktop Environments
---

### Post by arnab_das on 2009-09-22
I'm bit of a newbie here, so please help me out.

What exactly does "Screenlets/Desklets" mean?

Also, when I'm trying to install them from gnomelook, i cant, coz apparently I dont even have the "screenlets" folder under "/usr/local/share/"

Please help me out!

---

### Post by scragar on 2009-09-22
[http://tombuntu.com/index.php/2007/08/24/osx-like-widgets-with-ubuntu-screenlets-and-compiz-fusion/](http://tombuntu.com/index.php/2007/08/24/osx-like-widgets-with-ubuntu-screenlets-and-compiz-fusion/)

An old guide, but it does explain what they are better than I can. The command should work without having to edit your /etc/apt/sources.list Those sources are old now anyway.

---

### Post by arnab_das on 2009-09-22
> **scragar said:**
> [http://tombuntu.com/index.php/2007/08/24/osx-like-widgets-with-ubuntu-screenlets-and-compiz-fusion/](http://tombuntu.com/index.php/2007/08/24/osx-like-widgets-with-ubuntu-screenlets-and-compiz-fusion/)

An old guide, but it does explain what they are better than I can. The command should work without having to edit your /etc/apt/sources.list Those sources are old now anyway.


thanks a ton mate, but apparently its for older versions of Ubuntu, can u give me a link for Jaunty?

---

### Post by scragar on 2009-09-22
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Enable universe using that guide(It's not hard at all).
Install screenlets by clicking this link: [install screenlets](apt:screenlets)

Enjoy.

---

### Post by arnab_das on 2009-09-22
> **scragar said:**
> [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Enable universe using that guide(It's not hard at all).
Install screenlets by clicking this link: [install screenlets]("apt:screenlets")

Enjoy.


thanks mate, apparently synaptic manager had a screenlets installation option. so i installed it from there. but will i have to install the documentation as well?

btw screenlets are working fine as of now. using them and they're awesome!

---

### Post by scragar on 2009-09-22
If I'm not mistaken there should be a graphical manager for it under system>preferences.

Either way the actual docs wouldn't be too much use, but you can install them if you want:
```
apt-get install screenlets-doc
man screenlets
```

---

