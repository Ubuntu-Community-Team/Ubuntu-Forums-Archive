---
title: "Minimum xubuntu installation"
date: 2013-04-30
forum: Desktop Environments
---

### Post by flux242 on 2013-04-30
Hi,

I'm currently trying to build a minimum system that is ubuntu 13.04 based and has xubuntu-desktop on the top.

So first of all I installed the ubuntu base system using ubuntu mini.iso from [here]("http://cdimage.ubuntu.com/netboot/13.04/")

After that I installed xubuntu-desktop without recommended packages
```
sudo apt-get install --no-install-recommends xubuntu-desktop
```

Additionally I installed the following packages again without recommended packages
```
sudo apt-get install --no-install-recommends \
xfce4-terminal \
xfce4-power-manager \
xfce4-volumed \
xfce4-indicator-plugin \
xfce4-datetime-plugin \
xfce4-screenshooter \
xfce4-xkb-plugin \
xubuntu-icon-theme \
xfwm4-themes \
indicator-sound-gtk2 \
alacarte \
pavucontrol \
file-roller \
plymouth-theme-xubuntu-logo \
bluman \
bluez-hcidump
```

This results in almost perfect minimal xubuntu system!

What's missing are:
[LIST]
[*]Time and Date Settings (gnome-time-admin package)
[*]Users Settings (gnome-system-tools package)
[*]Network Manager (network-manager package)
[/LIST]

all these packages have heavy gnome packages dependencies (especially network-manager) and I'd like to find an alternative if any. Please suggest some

catfish is OK but it has a dependency to the zeitgeist package. Is there an alternative?

Did I forget to install some packages? Please comment

And I'm playing currently in the Virtual Box so any specific hardware drivers aren't installed. And no cups related packages installed.

---

### Post by claracc on 2013-05-01
Instead of network manager, I recommend to intall wicd, it is in the repositories and I think its footprint is smaller that network manager. [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

### Post by flux242 on 2013-05-01
> **claracc said:**
> Instead of network manager, I recommend to intall wicd,

yep, already installed it. The old good wicd - how could I forget about it!
Catfish can be installed from a ppa on the launchpad. It has zeitgeist crap in the suggests section!

---

### Post by arifalisyed on 2013-05-01
how much is your footprint now, after complete boot?
how many user processes are running after complete boot?
how many system process are running after complete boot?

Please check my machine's foot print [here]("http://ubuntuforums.org/showthread.php?t=2130640&page=4&p=12628356#post12628356").  
Back in my native people use very very old hardware with  128, 256, 512 MB RAMs, now all of their machines are unusable.
I was wondering if i could take your solutions to them?

---

### Post by flux242 on 2013-05-06
I have summarized my experience on this page [http://flux242.blogspot.com/2013/05/minimal-xubuntu-desktop-installation.html](http://flux242.blogspot.com/2013/05/minimal-xubuntu-desktop-installation.html)

---

### Post by zblace on 2013-05-27
Why not going ARCH Linux if you are looking at under 500MB RAM system?

---

