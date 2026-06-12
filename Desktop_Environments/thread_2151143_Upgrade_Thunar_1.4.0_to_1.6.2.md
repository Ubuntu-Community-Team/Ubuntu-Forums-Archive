---
title: "Upgrade Thunar 1.4.0 to 1.6.2"
date: 2013-06-03
forum: Desktop Environments
---

### Post by cmolinap1 on 2013-06-03
Hi,
How I can update Thunar 1.4.0 to 1.6.2 in Xubuntu 12.10? Until a few days ago it was possible using the following repository:
ppa.xubuntu-dev/xfce-4.12
Currently not working.

Thanks in advance.
cmolinap

---

### Post by dentaku65 on 2013-06-03
Thunar is available here:
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)
In order to use the dev Xfce you must set both PPA
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)
and
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12) 
```
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.10
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.12
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Dennis N on 2013-06-03
Xubuntu 12.04 was upgraded within the last few days to Thunar 1.6.3:

```
dn@Kayleigh:~$ apt-cache policy thunar
thunar:
  Installed: 1.6.3-0ubuntu1~ppa0.12.04.1
```

The source PPA was **xubuntu-dev/xfce-4.10**
I have no other xubuntu or xfce related ppa in my sources, so for thunar at least, this one alone is sufficient. The same is true for Xubuntu 12.10 on another machine.

---

