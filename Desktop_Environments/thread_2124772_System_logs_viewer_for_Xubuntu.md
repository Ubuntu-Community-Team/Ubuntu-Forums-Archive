---
title: "System logs viewer for Xubuntu"
date: 2013-03-12
forum: Desktop Environments
---

### Post by RockTeam on 2013-03-12
Is there any GUI application to view the system logs for Xubuntu? I like ***gnome-system-log***, but the downside is that it was included into the ***gnome-utils***, and after installing there are other unnecessary applications will apply to the system.

---

### Post by ibjsb4 on 2013-03-12
Weird

Gnome-system-log breaks/replaces gnome-utils on my system.

[ATTACH=CONFIG]240082[/ATTACH]

---

### Post by RockTeam on 2013-03-12
Sorry, I'm forgot to indicate that I use Xubuntu 10.04 and there is no standalone gnome-system-log package into repository.

---

### Post by ibjsb4 on 2013-03-12
> **RockTeam said:**
> Sorry, I'm forgot to indicate that I use Xubuntu 10.04 and there is no standalone gnome-system-log package into repository.

Did you find a PPA for it?  And added it to your sources list?  If so maybe you can get around that by not installing the recommended packages.

```
sudo apt-get install --no-install-recommends gnome-system-log
```

---

### Post by RockTeam on 2013-03-12
```
:~# apt-get install --no-install-recommends gnome-system-log
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-system-log
```

No it's not working. But I have found the source code of ***gnome-utils*** with the same version like in the official lucid repository here: [URL="http://ftp.acc.umu.se/pub/GNOME/sources/gnome-utils/2.30/"]http://ftp.acc.umu.se/pub/GNOME/sources/gnome-utils/2.30/
[/URL]
I build*** gnome-system-log ***from the source code without any additional unused packets. Now it's resolved.

Deb package is here: [http://www.fileswap.com/dl/VWz7pb5vE/](http://www.fileswap.com/dl/VWz7pb5vE/)

---

