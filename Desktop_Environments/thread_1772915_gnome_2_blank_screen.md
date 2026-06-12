---
title: "gnome 2 blank screen"
date: 2011-06-01
forum: Desktop Environments
---

### Post by pesardivooone on 2011-06-01
when i downgraded from gnome3 :

```

sudo apt-get install ppa-purge sudo ppa-purge ppa:gnome3-team/gnome3

```

i dont see my desktop in gnome 2 
and when i want to reinstall ubuntu-desktop , following error happen :

```

arash@arashpc:~$ sudo apt-get install ubuntu-desktop
[sudo] password for arash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: indicator-applet-session but it is not going to be installed
                  Recommends: network-manager-gnome but it is not going to be installed
E: Broken packages
arash@arashpc:~$ 

```

what should i do?
sorry for my bad english

---

### Post by Frogs Hair on 2011-06-01
I was noted at some of sites that posted the Gnome 3 PPA that re-installation would be required if you changed your mind . I don't if this has changed or not.

---

