---
title: "Ubuntu Server 16.04 install different desktop environments"
date: 2016-08-10
forum: Desktop Environments
---

### Post by tech291083 on 2016-08-10
Hi Friends,

I am running Ubuntu Server 16.04 LTS 32-bit and I would love to install different desktop environments, and I did try the following commands, but each time I got the following common error "E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)."

```

sudo apt-get install ubuntu-desktop

sudo apt-get install ubuntu-gnome-desktop

sudo apt-get install kubuntu-desktop

sudo apt-get install cinnamon xdm

sudo apt-get install mate-desktop-environment xdm xserver-xorg

sudo apt-get install lxde lxdm

sudo apt-get install xfce4 xdm


```

I must mention here that after installing Ubuntu, the 1st thing I did was to update the system with the following commands as root.

```

sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get dist-upgrade

```

What should I do?

Thanks.

---

### Post by egeezer on 2016-08-10
Do you have Xorg already?

---

### Post by deadflowr on 2016-08-11
Did you try the suggested solution:
```
sudo apt-get -f install
```
?

Also:
> I must mention here that after installing Ubuntu, the 1st thing I did was to update the system with the following commands as root.
```
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get dist-upgrade
```

were you already root?
if so, then if already root, no need to invoke sudo.
fwiw

---

