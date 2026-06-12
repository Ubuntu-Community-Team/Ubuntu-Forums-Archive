---
title: "No desktop after some uninstallation..."
date: 2010-02-18
forum: Desktop Environments
---

### Post by eNc707 on 2010-02-18
Hi there,

I installed Ubuntu 9.10 on a virtual machine and just wanna have a apache server. I installed the apache and everything worked fine until I unstalled several programs coming with the Ubuntu distribution.
The http server still works and i can connect via samba to my virtual machine/ubuntu but there is no graphical desktop environment. Take a look at the attached image what it actually looks like.

I searched via google and tried to install the ubuntu-desktop package and some other packages but they all already being installed.

Thx for help,

Frank

---

### Post by pmlxuser on 2010-02-18
may be u should explicitly indicate which programs you un installed and people would fins a better way of advising you

---

### Post by eNc707 on 2010-02-18
After reinstalling and reconfiguring ubuntu-desktop the desktop is at its place. But I don't wanna have open office, evolution mail, rythmbox and so on... how can I remove these packages without having problems with the desktop environment...?

Thx.

---

### Post by eNc707 on 2010-02-18
@pmlxuser: I want to remove games, all graphic tools, all internet programs except firefox, all office tools and I also do not need sound & video programs... so I uninstalled everything using synaptic package manager with the effect of a corrupted desktop...

---

### Post by pmlxuser on 2010-02-18
```

sudo apt-get purge openoffice evolution rythmbox 


```

remove the programs you want not the underlying system files. by specifying applic name in the purge command

---

### Post by nothingspecial on 2010-02-18
You cannot remove evolution without messing your ubuntu desktop.

The best method of achieving the set up you desire is to download and install the ubuntu minimal iso.

Then ```
sudo apt-get install install gnome-core gdm network-manager-gnome human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-utils firefox

```

Or if you don`t even want it to look like Ubuntu and want it as light as possible ```
sudo apt-get install wicd ncurses-bin ncurses-base xinit openbox firefox
```

And if you have no need for wireless forget wicd and ncurses (you don`t need them anyway it just makes it easier.

---

### Post by eNc707 on 2010-02-18
Thanks for help and special thanks to nothingspecial! :)

---

### Post by Weekendpartier on 2010-07-17
I am curious:  Did those commands work for you?

---

