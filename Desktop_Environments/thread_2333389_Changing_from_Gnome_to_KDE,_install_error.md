---
title: "Changing from Gnome to KDE, install error"
date: 2016-08-09
forum: Desktop Environments
---

### Post by brdmartin on 2016-08-09
This happened when I was trying to change from Gnome to KDE. It asked me a question that made no sense to this totally inexperienced linux user, and I figured that I had a slightly better chance of being correct if I chose the first of the 2 options. It had something to do with windows [which I need for a few programs], and maybe network managers, but I'm not really sure.

Here's what the terminal looked like when I typed the terminal command to install KDE again: 

```
brian@brian-XPS-8500:~$ sudo apt-get install kubuntu-desktop
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kubuntu-desktop is already the newest version (1.338).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

brian@brian-XPS-8500:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```


So I can't tell if this is a bug, or if I chose the wrong option when I tried to install KDE. As far as I can tell, I can't get into KDE, I've tried restarting and logging off. Please help.

---

### Post by QIII on 2016-08-09
Hello!

That indicates that you have more than one apt/dpkg interface open.  If you have a GUI open (Software Store, synaptic, etc), close it and try again.

---

### Post by kansasnoob on 2016-08-09
> **brdmartin said:**
> This happened when I was trying to change from Gnome to KDE. It asked me a question that made no sense to this totally inexperienced linux user, and I figured that I had a slightly better chance of being correct if I chose the first of the 2 options. It had something to do with windows [which I need for a few programs], and maybe network managers, but I'm not really sure.

Here's what the terminal looked like when I typed the terminal command to install KDE again: 

```
brian@brian-XPS-8500:~$ sudo apt-get install kubuntu-desktop
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kubuntu-desktop is already the newest version (1.338).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

brian@brian-XPS-8500:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```


So I can't tell if this is a bug, or if I chose the wrong option when I tried to install KDE. As far as I can tell, I can't get into KDE, I've tried restarting and logging off. Please help.

You needed to use sudo. This:

```
brian@brian-XPS-8500:~$ **[COLOR="#FF0000"]apt-get -f install[/COLOR]**
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

Should have been:

```
sudo apt-get -f install
```

That said it's not as easy as it used to be to change from one desktop environment to another. You might actually be better off to back up any important data and just perform a fresh install of Kubuntu.

---

