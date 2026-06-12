---
title: "Kubuntu with Xubuntu-desktop installed"
date: 2007-09-15
forum: Desktop Environments
---

### Post by cknight on 2007-09-15
I've been a solely Kubuntu user since converting to Linux and am now curious about other desktop managers/environments.  To that end, I'm now installing Xubuntu-desktop on top of my Kubuntu installation.  But this raises a few interesting questions:

1) What is the difference between installing Xubuntu-desktop on top of Kubuntu (and subsequently using the XFCE desktop environment) vs a clean installation of Xubuntu itself?

2) IceWM and FluxBox intrigue me.  However, these appear at first glance to my noob eye to be not as straightforward to install (i.e. there isn't an equivalent IceWM-desktop package presumably).  Are there any easy installation guides out there?

3) Any issues with having 3 or more desktop managers/environments loaded at once till I decide which is best?

4) Any other pitfalls to watch out for in playing around with other desktop managers?

Thanks!

---

### Post by Kilz on 2007-09-15
> **cknight said:**
> I've been a solely Kubuntu user since converting to Linux and am now curious about other desktop managers/environments.  To that end, I'm now installing Xubuntu-desktop on top of my Kubuntu installation.  But this raises a few interesting questions:

1) What is the difference between installing Xubuntu-desktop on top of Kubuntu (and subsequently using the XFCE desktop environment) vs a clean installation of Xubuntu itself?

2) IceWM and FluxBox intrigue me.  However, these appear at first glance to my noob eye to be not as straightforward to install (i.e. there isn't an equivalent IceWM-desktop package presumably).  Are there any easy installation guides out there?

3) Any issues with having 3 or more desktop managers/environments loaded at once till I decide which is best?

4) Any other pitfalls to watch out for in playing around with other desktop managers?

Thanks!

1. You will end up using a lot of hard drive space as the desktops take up lots of room.
2. I use icewm as the desktop for my server because its doesnt use a lot of resources. But its not as new user friendly as xfce, gnome, or kde. An example is that the menu isnt automatic. You have to add some applications manually. But with the rox filer and gtkedit its nice for editing and moving files around. As for guides. [The wiki]("https://help.ubuntu.com/community/IceWM?highlight=%28icewm%29") is [your friend]("https://help.ubuntu.com/community/Installation/LowMemorySystems")
3. Other than a lot of space used, no. But I would use aptitude to install/remove them as it does a better job of cleaning out what it installs. ```
sudo aptitude install xubuntu-desktop
``` would install ```
sudo aptitude remove xubuntu-desktop
``` to remove.

---

