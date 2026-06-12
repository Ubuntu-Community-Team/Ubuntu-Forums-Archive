---
title: "Installing kubuntu in ubuntu from CD"
date: 2008-06-28
forum: Desktop Environments
---

### Post by lunamystry on 2008-06-28
I didn't think it'd be hard. I'm a fan of Kubuntu actually i don't like kubuntu i like Ubuntu but i prefer KDE. So i have Ubuntu installed. Gnome being gnome i want kde again. I thus ordered a kubuntu cd from shipit then i realised i have enough things in gnome to keep it. Now i am thinkin maybe with essential build or something i can install kubuntu-desktop and ubuntu-desktop together and switch as i please. the max i download from the internet is twenty megabytes. i hope it is possible.

---

### Post by aysiu on 2008-06-28
You need the Kubuntu Alternate CD, not the Desktop CD.

My guess is that you got sent the Desktop CD.

Find some way to get a hold of the Alternate CD and then paste these commands into the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.noncd
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
sudo mv /etc/apt/sources.list /etc/apt/sources.list.cd
sudo mv /etc/apt/sources.list.noncd /etc/apt/sources.list
```

---

### Post by prshah on 2008-06-28
> **aysiu said:**
> 
```
[color=red]sudo mv /etc/apt/sources.list /etc/apt/sources.list.noncd[/color]
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
[color=blue]sudo mv /etc/apt/sources.list /etc/apt/sources.list.cd
sudo mv /etc/apt/sources.list.noncd /etc/apt/sources.list[/color]
```

These commands will also work with the kubuntu live CD. 

The first one (in red) may not need to be done; if the kubuntu-desktop metapackage is found on CDROM and the CDROM is enabled, (and it will be with the above commands) then it will pull the packages off the CD instead of the Internet.

As a corollary, the last two commands (in blue) also don't need to be used if you don't use the first one.

Updates are another matter; you will easily run into 100+ mb of updates, and some (especially openssl related) are essential.

---

### Post by aysiu on 2008-06-28
No, they won't work on the Desktop CD. The Desktop CD does not contain all the packages needed to install Kubuntu.

---

### Post by lunamystry on 2008-08-19
Its only right that i post this. I finally got my hands on an alternate install cd and ran the commands above. Kubuntu-kde4-desktop was installed and i have regret. my pc is not connected to the internet so no updates all year. i recently used my phone as a modem and then i was asked to update. this would have been too expensive so i just left it. i think this made apt remove synaptic, nautilus and some other gnome components. i am not complaining because i was asked if this was okay and i said yes. now i have kde4, an unusable openoffice, not so usable gnome enviroment and still no amarok. my screen resolution sucks and i cnt fix it. so now i am waiting for interib ibex so i can make a clean install.

---

