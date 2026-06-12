---
title: "Kubuntu, Ubuntu and Xubuntu combined?"
date: 2007-12-03
forum: Desktop Environments
---

### Post by Schalken on 2007-12-03
What would happen if I installed the metapackages "ubuntu-desktop", "kubuntu-desktop" and "xubuntu-desktop" all on the same system?

Do the packages conflict?

Once they are installed, which theme do I get for the bootsplash/usplash, and which display manager get's used? (KDM or GDM or whatever Xfce uses (GDM?))

And what is the default desktop for new users of the system?

---

### Post by funpop on 2007-12-03
they live happily together, and you should be asked which one you want as login manager. there you choose your session (xfce, gnome, kde). 

not really sure, but i think the default will be the one you used to install the others. no idea what heppens if you add them to a command-line install..

prepare for some really huge menu's :)

---

### Post by Schalken on 2007-12-03
:lolflag: huge menus indeed.

Thanks, at least I know it wont break. But I'll see what happens to the default login manager/usplash/desktop environment when I do it. At the moment it looks like it will keep the default from the initial install, and the default will be changable later on somehow. (I dont know how though.)

---

### Post by funpop on 2007-12-03
i use kde, the default session is always the last used. i think you have the option to safe a specific session as your default..

---

### Post by Schalken on 2007-12-09
I've installed all three metapackages on this system and it *works* fine. In some cases, it doesn't *look* fine, though. All the KDE configurations modules appear in GNOME under Applications > Other, to make a list twice the height of my screen, and all the GNOME configuration modules appear in KDE's menu in different places and are mostly missing their icons.

When the kubuntu-desktop package was installed, it set my usplash theme to Kubuntu's :(, however, it did ask me which display manager I want to run, at least. But when the GDM package is configured, such as during the installation of either the xubuntu-desktop or kubuntu-desktop metapackages, it set the GDM theme to Xubuntu's and I have to change it back.

But other than the menu's I am overal happy with the result. I just wish KDE apps would integrate a little better with GNOME :P

---

### Post by steve-de-buntu on 2007-12-26
This is sort of what I'm looking at doing to work out which DE would work best for me 

(have a inspiron 6400 laptop with c2d and soon to be 2gb of ram, but am coming from really bad experiences with vista lag - hence the desire to experiment with xfce as well)

tell me, having installed all three of the de's, would it be too difficult to configure the menu's so that only the appropriate items appear when you choose a session (i.e. xfce, gnome kde)? - so for example only gnome menus appear when you're using the gnome de?

must admit I'm a bit confused as to why the menus would be so long..

Steve

---

### Post by dlegend on 2007-12-27
> **steve-de-buntu said:**
> This is sort of what I'm looking at doing to work out which DE would work best for me 

(have a inspiron 6400 laptop with c2d and soon to be 2gb of ram, but am coming from really bad experiences with vista lag - hence the desire to experiment with xfce as well)

tell me, having installed all three of the de's, would it be too difficult to configure the menu's so that only the appropriate items appear when you choose a session (i.e. xfce, gnome kde)? - so for example only gnome menus appear when you're using the gnome de?

must admit I'm a bit confused as to why the menus would be so long..

Steve

For removing KDE apps from the gnome menu and vice-versa run the script "menu-cleaner.sh" (provided at the end of this post). If you are worried that it may screw up your menu just make a backup copy of those directories:

> 
    mkdir -p ~/.menu-backup/{gnome,kde}

    cp /usr/share/applications/* ~/.menu-backup/gnome

    cp /usr/share/applications/kde/* ~/.menu-backup/kde


Script: [http://www.programming-designs.com/linux/menu-cleaner.sh](http://www.programming-designs.com/linux/menu-cleaner.sh)

I got this info from [this link](http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/) but their tutorial doesn't work for Gutsy and the menu-cleaner script is no longer available on their site.

Enjoy =)

---

### Post by steve-de-buntu on 2008-01-10
Thanks! Will give it a go.

---

